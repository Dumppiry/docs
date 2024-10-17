# Documentation pages

Documentation for all the projects of Dumppi Ry

## Writing docs

Here is all you need to know to start writing these docs. There is two main ways to write/develop this documentation site. Firstly you can just add/edit files under the `docs/_projects` to modify just the documentation pages. The files are all `.md` files and they start with the yaml template followed by the content written in markdown.

The second way is if you want to develop the site. If you want to make modifications to the docs site, then install all requirements and make sure you get the local development server up and running so you can test and see the outcome.

### Presequisites

If you want to use live server to preview the docs site, you will need the following software:

- Ruby
- Bundler
- Make
- build-essential
- zlib1g-dev

Install Ruby. Check out the [installation](https://www.ruby-lang.org/en/documentation/installation/) page for how to do this. For Ubuntu/Debian you can install it with following command:

```bash
sudo apt install ruby-full build-essential zlib1g-dev make
```

Lets not install gems globally. For this we have to change gemhome. Following works for Ubuntu/Debian. For other options see the documentation of [Jekyll](https://jekyllrb.com/docs/installation/)

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Install bundler.

```bash
gem install bundler
```

Next you need to install the gems needed. Firstly cd to docs directory.

```bash
cd docs
```

After you are in correct directory you can install with the bundler.

```bash
bundle install
```

Now you are ready to launch the dev server with:

```bash
make dev
```
