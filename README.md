# Selenium ChromeDriver Cookbook

[![Cookbook Version](http://img.shields.io/cookbook/v/chromedriver.svg?style=flat-square)][supermarket]
[![Build Status](http://img.shields.io/travis/dhoer/chef-chromedriver.svg?style=flat-square)][travis]

[supermarket]: https://supermarket.chef.io/cookbooks/chromedriver
[travis]: https://travis-ci.org/dhoer/chef-chromedriver

Installs ChromeDriver (https://github.com/SeleniumHQ/selenium/wiki/ChromeDriver). 

## Requirements

- Chef 11.16+
- Chrome (this cookbook does not install Chrome)

### Platforms

- CentOS, RedHat
- Mac OS X
- Ubuntu
- Windows

### Cookbooks

- windows 

## Usage

Include recipe in a run list or cookbook to install ChromeDriver.

### Attributes

- `node['chromedriver']['version']` - Version to download. Default `LATEST_RELEASE`.
- `node['chromedriver']['url']` -  URL download prefix. Default `https://chromedriver.storage.googleapis.com`.
- `node['chromedriver']['windows']['home']` - Home directory for windows. Default `%SYSTEMDRIVE%\chromedriver`.
- `node['chromedriver']['unix']['home']` - Home directory for both linux and macosx. Default `/opt/chromedriver`.

#### Install selenium node with chrome capability

```ruby
include_recipe 'chrome'
include_recipe 'chromedriver'

node.set['selenium']['node']['capabilities'] = [
  {
    browserName: 'chrome',
    maxInstances: 1,
    version: chrome_version,
    seleniumProtocol: 'WebDriver'
  }
]

include_recipe 'selenium::node'
```

#### Download ChromeDriver from alternative location

```
override_attributes(
  "chromedriver": {
    "url": "https://s3.amazonaws.com/mybucket/chromedriver"
    "version": "2.21"
  }
)
```

This will download the ChromeDriver that best matches version and platform criteria e.g., Linux x64 platform will 
match https://s3.amazonaws.com/mybucket/chromedriver/2.21/chromedriver_linux64.zip. Note that ChromeDriver path must 
be the same as that found under http://chromedriver.storage.googleapis.com/index.html.

## Getting Help

- Ask specific questions on [Stack Overflow](http://stackoverflow.com/questions/tagged/chromedriver).
- Report bugs and discuss potential features in [Github issues](https://github.com/dhoer/chef-chromedriver/issues).

## Contributing

Please refer to [CONTRIBUTING](https://github.com/dhoer/chef-chromedriver/blob/master/CONTRIBUTING.md).

## License

MIT - see the accompanying [LICENSE](https://github.com/dhoer/chef-chromedriver/blob/master/LICENSE.md) file for 
details.
