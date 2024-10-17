---
layout: default
title: Sanity Docs
permalink: /sanity-docs/
---

# Sanity documentation

Here I try to explain the basics of our CMS system Sanity. For extensive documentation you should read the Sanitys own [documentation](https://www.sanity.io/docs).

Sanity is highly customizable content management system which can be build to match the needs of the user. It is client side web application and stores the data to Sanitys cloud. Data can be edited via Sanity studio or via API (not recommended). We have build our own studio and it is found at [github](https://github.com/Dumppiry/studio). This is not yet a public project. We try to publish it as open source as soon as possible. For now, request access to the repo from current Webmaster of Dumppi Ry.

Webmaster can administrate the users for our Sanity Studio and also create tokens for development and CI/CD purposes. User access is needed for ability to login to Studio and manage the content via web UI. API tokens are used to access the content lake programmatically. Contact Webmaster for hopes and wishes regarding to user access and tokens.

## Data structure of Sanity

Data is stored to Sanity as Documents in the [Sanity Content Lake](https://www.sanity.io/docs/datastore). Data in the content lake can be accessed via [HTTP API](https://www.sanity.io/docs/http-api) or via [client libraries](https://www.sanity.io/docs/client-libraries). Documents are stored in `datasets`. You can think the datasets as a containers which hold the data related to one thing. At our Sanity we have 2 datasets so far. One called `production` which has the data of our website and another named `dumppi-sides` which holds the data for our different side projects. Datasets help you to create seperation between contents you do not wish to mix.

In datasets we store the `Documents`. Documents have a `_type` which can be used to fetch multiple documents of of same type. For example we have a document type `event` for our website and we can query all our events by using that doc type. Each different doc type describes the structure of the instances of the document. This structure or "[Schema](https://www.sanity.io/docs/schema-types)" of the document is defined in the Studio source code. The schema of the doc type defines all the fields and the types of data the field holds for the doc type.

[Objects](https://www.sanity.io/docs/object-type) are the main way to define the datamodels. Object is a model which describes the structure of the data. The way we define objects is pretty much the same as the way we define schemas in the source code of the Studio. The key difference is the `type` field in the schema. For objects the field must be `object` in contrast to `document` for documents. The key difference between Object and Document is that each document is saved as its own document but each object is saved to the document for which they belong to.

## Querying Sanity

Sanitys content lake uses [GROQ](https://www.sanity.io/docs/groq) as a query language. You can test your queries with the Vision tool in the studio. In the code you can use Sanitys API clients or the HTTP API.

> Note about Next.js: As of 17.10.2024 Sanitys js client librarys Fetch method does not work with Next.js static site generation. The problem is that Next.js counts the clients Fetch as a server side method and does not allow it to be used in ssg. Use manual HTTP request instead with Sanitys HTTP API.

For extensive syntax and documentation, refer to Sanitys [documentation](https://www.sanity.io/docs/groq). Here are some basic queries to get the hang of it:

```groq
*[]                                                     // This query gets all the documents found in the dataset.

*[_type == "event"]                                     // Queries all the documents with the document type of 'event'

*[_type == "event"] {
    ...,                                                // This means we get all the fields from the events
    "registrationCount": registrationSubmissions.length // then we also add new custom field showing the number of registrations.
}

*[_type == "event"] {
    ...,
    "referencedPerson" -> contactPerson {
        name,
        email
    }
} // Here we fetch events and as they have field "contactPerson" which is reference to another document, we fetch the name and email of the referenced contactPerson.
```
