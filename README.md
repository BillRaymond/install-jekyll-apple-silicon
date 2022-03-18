# This is the documentation for my YouTube video, titled "Install Jekyll on Apple Silicon"
Video: [Install Jekyll on Apple Silicon](https://studio.youtube.com/channel/UCo63gWfWRfEciJ98mJLIU0Q)


## Install homebrew
Think of Homebrew as an app store for the command line. Everything you install for Jekyll will be free and open source.
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Finalize homebrew
Note: be sure to replace `[username]` with the username you use on your Mac.
```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/[yourusername]/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
export SDKROOT=$(xcrun --show-sdk-path)
```

## Install Ruby 3.0.x
You can see the version of Ruby pre-installed with your Mac, by typing:
```
ruby -v
```

### You will need to install your own copy of Ruby using Homebrew with the following command:
```
brew install ruby@3.0
```

### Finalzie the Ruby installation
Type:
```
echo $SHELL
```

The result will be `zsh` or `bash`

For zsh, type:
```
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
```

For bash, type:
```
echo 'export PATH="$HOME/.gem/ruby/X.X.0/bin:$PATH"' >> ~/.bash_profile
```

Type:
```
exit
```

Quit terminal

Run terminal again and type: 
```
ruby -v
```
(make sure it is ruby 3.0.x)

## Install Jekyll and Bundler
Type:
```
gem install --user-install bundler jekyll
```

Type:
```
echo $SHELL
```

For zsh, type:
```
echo 'export PATH="$HOME/.gem/ruby/3.0.0/bin:$PATH"' >> ~/.zshrc
```

For bash, type:
```
echo 'export PATH="$HOME/.gem/ruby/3.0.0/bin:$PATH"' >> ~/.bash_profile
```

Type:
```
gem env
```
Look for the "GEM PATHS" section and make sure they all refer to 3.0.0

### Create a folder for your new Jekyll site
Type:
```
cd desktop
mkdir jekylltest
cd jekylltest
```

### If you are even thinking of using Git, create a .gitignore file
Create a `.gitignore` file at the rooy of your `jekylltest` folder

Add the following lines to the file:
```
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata
**/.DS_Store
.bundle/
vendor/
```

### Create a Jekyll site based on the default Minima theme
You will create a Jekyll site based on the default Minima theme that ships with Jekyll.
If you want to choose a different type of site (different theme, blank site, etc), follow this link:
https://jekyllrb.com/docs/usage

Type:
```
bundle init
bundle add jekyll --version "~>4.2"
bundle config set --local path 'vendor/bundle'
bundle install
bundle exec jekyll new --force --skip-bundle .
bundle add webrick
bundle install
bundle update
```

## Run the Jekyll site
```
bundle exec jekyll serve --livereload
```
Copy the resulting URL (it usually ends in `4000`)
Paste the text into a browser
The site should run!


