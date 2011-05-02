# Deploying Zend Framework applications with zend-framework-deploy

Tired to manually deploy your Zend Framework projects, this gem is for you. It will use
the Capistrano framework adapted to fit ZF structure and files and removes Rails specific tasks.

## Installation

    $ gem install zend-framework-deploy

## Usage

    $ cd your-zf-project-root && zf-capify .

This command will create the required files inside your ZF project. You can also use `-m` switch to
use the [multistage extension](https://boxpanel.bluebox.net/public/the_vault/index.php/Capistrano_Multi_Stage_Instructions)
of capistrano. The `-m` switch accepts a comma separated list of stages to create.

## Requirements

It depends on `capistrano` gem. If you want multistage support you should also install
`capistano-ext` gem (it's not listed as dependency). [RVM](http://rvm.beginrescueend.com/) is
strongly advised to install Ruby and RubyGems.

## What tasks are included in the gem?

These are the tasks adapted for Zend Framework projects included in my gem

    cap deploy               # Deploys your project.
    cap deploy:check         # Test deployment dependencies.
    cap deploy:cleanup       # Clean up old releases.
    cap deploy:install_zf    # Install Zend Framework in library path for the dep...
    cap deploy:pending       # Displays the commits since your last deploy.
    cap deploy:pending:diff  # Displays the `diff' since your last deploy.
    cap deploy:rollback      # Rolls back to a previous version and restarts.
    cap deploy:rollback:code # Rolls back to the previously deployed version.
    cap deploy:setup         # Prepares one or more servers for deployment.
    cap deploy:symlink       # Updates the symlink to the most recently deployed ...
    cap deploy:update        # Copies your project and updates the symlink.
    cap deploy:update_code   # Copies your project to the remote servers.
    cap deploy:upload        # Copy files to the currently deployed version.
    cap invoke               # Invoke a single command on the remote servers.
    cap shell                # Begin an interactive Capistrano session.
    cap web:disable          # Present a maintenance page to visitors.
    cap web:enable           # Makes the application web-accessible again.

## Zend Framework installation

This gem provides a task named deploy:install_zf which is called by default deploy. This task relies on
`zf_path` capistrano variable, so you must provide it in your `deploy.rb` file. This variable should contain
the path for the ZF release, or if you have more than one version of ZF in your server, the base path for the
installations. In the latter case you should have a dir structure like this one (in my case `zf_path` is set
to `'/var/zend/`)

    $ ls /var/zend/
    ZendFramework-1.11.0
    ZendFramework-1.11.5

When you're following this convention you can use a file in your scm to control what version of ZF is copied
in the library folder. To achieve this simply drop a file named `zf.version` in your `application/configs` folder
 containing the required ZF version and the corresponding version is linked in your library folder.

This approach works as far as your `index.php` contains the code generated from the zf tool, i.e. the following
snippet of code is executed before requiring any ZF class.

    // Ensure library/ is on include_path
    set_include_path(implode(PATH_SEPARATOR, array(
        realpath(APPLICATION_PATH . '/../library'),
        get_include_path(),
    )));

I prepared a sample empty zf-capified application on github, you can fork it [here](https://github.com/fabn/zf-capified-sample)

## Thanks to

* Lee Hambley for his [Railsless Deploy Gem](https://github.com/leehambley/railsless-deploy)

## Contributing to zend-framework-deploy
 
* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it
* Fork the project
* Start a feature/bugfix branch
* Commit and push until you are happy with your contribution
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.

## Copyright

Copyright (c) 2011 Fabio Napoleoni. See LICENSE.txt for
further details.

