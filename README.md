## How to generate `Realm.framework`

```
$ git clone git@github.com:realm/realm-cocoa.git
$ cd realm-cocoa
$ /bin/sh build.sh build
```

`Realm.framework` is built in `build/ios/Realm.framework`, then copy it into RubyMotion project.

## Configure RubyMotion app

1. Copy `Realm.framework` into `vendor` directory.
2. Configure `Rakefile` for RubyMotion app as below.

```ruby
  app.vendor_project('vendor/Realm.framework', :static,
    :products => ['Realm']
  )
  app.archs['iPhoneOS'] = ['armv7']
```

`Realm.framework` has the following architecture types in binary, it does not contain `armv7s`. So, it neeed to remove `armv7s` for device. RubyMotion app is built `armv7` and `armv7s` for device by default.

```
$ file build/ios/Realm.framework/Realm
/Users/watson/src/github/realm-cocoa/build/ios/Realm.framework/Realm: Mach-O universal binary with 4 architectures
/Users/watson/src/github/realm-cocoa/build/ios/Realm.framework/Realm (for architecture armv7):	current ar archive random library
/Users/watson/src/github/realm-cocoa/build/ios/Realm.framework/Realm (for architecture i386):	current ar archive random library
/Users/watson/src/github/realm-cocoa/build/ios/Realm.framework/Realm (for architecture x86_64):	current ar archive random library
/Users/watson/src/github/realm-cocoa/build/ios/Realm.framework/Realm (for architecture cputype (16777228) cpusubtype (0)):	current ar archive random library
```