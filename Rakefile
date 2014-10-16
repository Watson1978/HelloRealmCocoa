# -*- coding: utf-8 -*-
$:.unshift("/Library/RubyMotion/lib")
require 'motion/project/template/ios'

begin
  require 'bundler'
  Bundler.require
rescue LoadError
end

Motion::Project::App.setup do |app|
  # Use `rake config' to see complete project settings.
  app.name = 'HelloRealmCocoa'
  app.vendor_project('vendor/Realm.framework', :static,
    :products => ['Realm']
  )
  app.archs['iPhoneOS'] = ['armv7']
end
