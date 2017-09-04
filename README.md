# Hexo Admin

## Preparation
Install  Node

`brew install node`

Update npm if needed

`npm i -g npm`

Install Hexo

`npm install hexo-cli -g`

## Dealing with Hexo
Get code from GitHub. And switch to `admin` branch.
```
git clone https://github.com/nickcheng/nickcheng.github.io.git
git checkout admin
```

I'm using the theme `Next`. And in the code, I use the theme as a git submodule. We need get the source code of the theme as well.
```
git submodule init
git submodule update
```

In the folder, install modules

`npm install`

If the source is already there, just need update the modules

`npm update`

## Configuration
Since the submodule need keep update with the upstream, my personal configuration saved in the `theme` folder. So after get the latest code of the theme, need copy/migrate the configuration file to specific theme folder. You might need do

`cp themes/_config.yml themes/next/`
