---
layout: post
title: "Build gem note"
date: 2016-01-15 02:15:45 +0800
comments: true
categories: tech
---

嘗試自己做gem，但是build完之後，會出現

```
LoadError: cannot load such file -- weatherscout
from /Users/Hsnl/.rvm/rubies/ruby-head/lib/ruby/site_ruby/2.3.0/rubygems/core_ext/kernel_require.rb:54:in `require'
```

後來發現是因為lib底下最上層的檔案沒有跟gem的名字一樣
下面 tree 中兩個粗體字就是應該要跟gem名稱一樣

```
.
├── Gemfile
├── Gemfile.lock
├── LICENSE.txt
├── README.md
├── Rakefile
├── bin
│ └── weatherscout <==
├── lib
│ ├── weatherdesc
│ │ ├── daily_weather.rb
│ │ └── version.rb
│ └── weatherscout.rb <==
├── spec
│ └── weatherdesc_spec.rb
└── weatherscout.gemspec <==
```

未來想改善一下weatherscout model的部分
想加入weekly weather，而weekly和daily又有好多重複的部分，還沒決定這邊怎麼處理
但是應該都會放在同一個module裡面
這裡memo一下想用的寫法，將同個module的class放在不同檔案(dependency一向有點麻煩)

http://stackoverflow.com/questions/12035057/breaking-ruby-module-across-several-files


另外version要怎麼update也另外記在這

Semantic Versioning (semver.org): MAJOR.MINOR.PATCH
http://semver.org

Increment the:

- MAJOR version when you make incompatible API changes,
- MINOR version when you add functionality in a backwards-compatible manner, and
- PATCH version when you make backwards-compatible bug fixes.
