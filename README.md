# ChefCollection handler
Print the resource collection, immediate notification collection, and delayed
notification collection from the Chef run.

## Usage
Either just pull the handler file into a files directory of one of your
cookbooks, or download as a Rubygem and source it that way.

```ruby
# Option 1
cookbook_file "#{node[:chef_handler][:handler_path]}/chef-handler-collection.rb" do
  source 'chef-handler-collection.rb'
  mode 00600
end

chef_handler 'ChefCollection' do
  source "#{node[:chef_handler][:handler_path]}/chef-handler-collection.rb"
  action :enable
end

# Option 2
chef_gem 'chef-handler-collection' do
  action :install
end

chef_handler 'ChefCollection' do
  source ::File.join(Gem.all_load_paths.grep(/chef-handler-collection/).first,
                     'chef-handler-collection.rb')
  action :enable
end
```

### Arguments
* `resources` - Should the handler print all the resources (default: `true`)
* `immediate` - Should the handler print all immediate notifications (default: `true`)
* `delayed` - Should the handler print all delayed notifications (default `true`)

## Author and License
Simple Finance <ops@simple.com> (##simple on Freenode)
Apache License, Version 2.0

