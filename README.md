"Comité des fêtes de Râches" website
====================================

# Presentation

The "_Comité des fêtes de Râches_" (translated _Râches Festival Committee_ in English from French) is a non-profit organization that organizes events in the village of Râches (59194, France). It is composed of volunteers who are passionate about their village and who want to make it live.
This organization is managed by Thierry Meresse, president of the association. Please [contact him](https://fetes-raches.fr/contact/) (French language only) for any information about the association. For any issue about this website, please [open an issue](https://github.com/Comite-des-fetes-de-Raches/Comite-des-fetes-de-Raches/issues/new) on this repository.

The URL of the website is : https://fetes-raches.fr

This website is a static website generated with [Jekyll](https://jekyllrb.com/). It is hosted on [Github Pages](https://pages.github.com/).

# Installation

This website is generated with Jekyll. To install it, you need to install Jekyll and its dependencies.

Following instructions is a copy from [Jekyll documentation](https://jekyllrb.com/docs/installation/).

## Dev environment

### Install (Linux - Ubuntu)

Install Ruby and other prerequisites:

```sh
sudo apt-get install ruby-full build-essential zlib1g-dev
```

Avoid installing RubyGems packages (called gems) as the root user. Instead, set up a gem installation directory for your user account. The following commands will add environment variables to your `~/.bashrc` file to configure the gem installation path:

```sh
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
Finally, install Jekyll and Bundler:

```sh
gem install jekyll bundler
```

That’s it! You’re ready to start using Jekyll.

### Install (Windows)

While Windows is not an officially-supported platform, it can be used to run Jekyll with the proper tweaks.

#### Installing Ruby and Jekyll

##### Installation via RubyInstaller

The easiest way to install Ruby and Jekyll is by using the [RubyInstaller](https://rubyinstaller.org/) for Windows.

RubyInstaller is a self-contained Windows-based installer that includes the Ruby language, an execution environment,
important documentation, and more.

We only cover RubyInstaller-2.4 and newer here. Older versions need to
[install the Devkit](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit) manually.

1. Download and install a **Ruby+Devkit** version from [RubyInstaller Downloads](https://rubyinstaller.org/downloads/).
   Use default options for installation.
2. Run the `ridk install` step on the last stage of the installation wizard. This is needed for installing gems with native
   extensions. You can find additional information regarding this in the
   [RubyInstaller Documentation](https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system).
   From the options choose `MSYS2 and MINGW development tool chain`.
3. Open a new command prompt window from the start menu, so that changes to the `PATH` environment variable becomes effective.
   Install Jekyll and Bundler using `gem install jekyll bundler`
4. Check if Jekyll has been installed properly: `jekyll -v`

You may receive an error when checking if Jekyll has not been installed properly. Reboot your system and run `jekyll -v` again.
If the error persists, please open a [RubyInstaller issue](https://github.com/oneclick/rubyinstaller2/issues/new).

That's it, you're ready to use Jekyll!

##### Installation via Bash on Windows 10

If you are using Windows 10 version 1607 or later, another option to run Jekyll is by
[installing](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide) the Windows Subsystem for Linux.

You must have [Windows Subsystem for Linux](https://msdn.microsoft.com/en-us/commandline/wsl/about) enabled.

Make sure all your packages and repositories are up to date. Open a new Command Prompt or PowerShell window and type `bash`.

Your terminal should now be a Bash instance. Next, update your repository lists and packages:

```sh
sudo apt-get update -y && sudo apt-get upgrade -y
```

Next, install Ruby. To do this, let's use a repository from [BrightBox](https://www.brightbox.com/docs/ruby/ubuntu/),
which hosts optimized versions of Ruby for Ubuntu.

```sh
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf
```

Next, update your Ruby gems:

```sh
gem update
```

Install Jekyll:

```sh
gem install jekyll bundler
```

No `sudo` here.

Check your Jekyll version:

```sh
jekyll -v
```

That's it! You're ready to start using Jekyll.

You can make sure time management is working properly by inspecting your `_posts` folder. You should see a markdown file
with the current date in the filename.

#### Encoding

If you use UTF-8 encoding, Jekyll will break if a file starts with characters representing a [BOM](https://en.wikipedia.org/wiki/Byte_order_mark#UTF-8). Therefore, remove this sequence of bytes if it appears at the beginning of your file.

Additionally, you might need to change the code page of the console window to UTF-8 in case you get a
`Liquid Exception: Incompatible character encoding` error during the site generation process. Run the following:

```sh
chcp 65001
```

#### Time Zone Management

Since Windows doesn't have a native source of zoneinfo data, the Ruby Interpreter doesn't understand IANA Timezones.
Using them had the `TZ` environment variable default to UTC/GMT 00:00.

Though Windows users could alternatively define their blog's timezone by setting the key to use the POSIX format of defining
timezones, it wasn't as user-friendly when it came to having the clock altered to changing DST-rules.

Jekyll now uses a rubygem to internally configure Timezone based on established
[IANA Timezone Database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

While 'new' blogs created with Jekyll v3.4 and greater, will have the following added to their `Gemfile` by default, existing
sites *will* have to update their `Gemfile` (and installed gems) to enable development on Windows:

```ruby
# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end
```

#### Auto Regeneration

Jekyll uses the `listen` gem to watch for changes when the `--watch` switch is specified during a build or serve.
While `listen` has built-in support for UNIX systems, it may require an extra gem for compatibility with Windows.

Add the following to the `Gemfile` for your site if you have issues with auto-regeneration on Windows alone:

```ruby
gem 'wdm', '~> 0.1.1', :install_if => Gem.win_platform?
```

You have to use a [Ruby+Devkit](https://rubyinstaller.org/downloads/) version of the RubyInstaller and install
the MSYS2 build tools to successfully install the `wdm` gem.

### Install (MacOS)

#### Supported macOS versions
- Ventura (macOS 13)
- Monterey (macOS 12)
- Big Sur (macOS 11)

Older macOS versions might work, but we don’t officially support them.

#### Install Ruby

To install Jekyll on macOS, you need a proper Ruby development environment. While macOS comes preinstalled with Ruby, we don’t recommend using that version to install Jekyll. This external article goes over the various reasons why you shouldn’t use the system Ruby.

Instead, you’ll need to install a separate and newer version of Ruby using a version manager such as asdf, chruby, rbenv, or rvm. Version managers allow you to easily install multiple versions of Ruby, and switch between them.

We recommend chruby because it’s the simplest and least likely to cause issues.

The instructions below are an excerpt from this detailed external guide to install Ruby on Mac. They work best if you’re setting up development tools for the first time on your Mac. If you’ve already tried to install Ruby or Jekyll on your Mac, or if you run into any issues, read that guide.

##### Step 1: Install Homebrew

Homebrew makes it easy to install development tools on a Mac.
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

##### Step 2: Install `chruby` and the latest Ruby with `ruby-install`
Install `chruby` and `ruby-install` with Homebrew:

```sh
brew install chruby ruby-install xz
```

Install the latest stable version of Ruby (supported by Jekyll):

```sh
ruby-install ruby 3.1.3
```
This will take a few minutes, and once it’s done, configure your shell to automatically use `chruby`:

```sh
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.1.3" >> ~/.zshrc # run 'chruby' to see actual version
```

If you’re using Bash, replace `.zshrc` with `.bash_profile`. If you’re not sure, read this external guide to find out which shell you’re using.

Quit and relaunch Terminal, then check that everything is working:

ruby -v
It should show ruby 3.1.3p185 (2022-11-24 revision 1a6b16756e) or a newer version.

Next, read that same external guide for important notes about setting and switching between Ruby versions with chruby.

##### Install Jekyll
After installing Ruby with chruby, install the latest Jekyll gem:

```sh
gem install jekyll
```

### Lunch website in dev environment for all OS

1. Install the jekyll and bundler gems.
```sh
gem install jekyll bundler
```
2. Clone this repository.
```sh
git clone git@github.com:Comite-des-fetes-de-Raches/Comite-des-fetes-de-Raches.git
```
3. Change into your new directory.
```sh
cd Comite-des-fetes-de-Raches
```
4. Build the site and make it available on a local server.
```sh
bundle exec jekyll serve
```
5. Browse to [http://localhost:4000](http://localhost:4000)
