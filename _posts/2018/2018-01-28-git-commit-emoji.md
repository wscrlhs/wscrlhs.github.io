---
layout: post
title:  git commit 时emoji表情的使用
categories: git emoji 
tags:  git emoji
---

* content
{:toc}


在`git commit` 时使用emoji表情,为本次提交贴上一个标签。既生动有趣，又能使得提交信息一目了然。
但是，emoji表情不能乱用，否则容易造成误解。因此开源项目 [gitmoji](https://gitmojicarloscuestame/) 专门规定了在 github 提交代码时应当遵循的 emoji 规范：

![](/assets/images/20180128001.png)




## commit格式 . 
>:emoji1: :emoji2: Subject   
>(Only One NewLine)   
>Message Body  
>(Only One NewLine)   
>Ref <###>   


## emojis

| Emoji | Raw Emoji Code                | Description                              |
| ----- | ----------------------------- | ---------------------------------------- |
| 🎨    | `:art:`                       | Improving structure / format of the code |
| ⚡️    | `:zap:`                       | Improving performance                    |
| 🔥    | `:fire:`                      | Removing code or files                   |
| 🐛    | `:bug:`                       | Fixing a bug                             |
| 🚑    | `:ambulance:`                 | Critical hotfix                          |
| ✨     | `:sparkles:`                  | Introducing new features                 |
| 📝    | `:memo:`                      | Writing docs                             |
| 🚀    | `:rocket:`                    | Deploying stuff                          |
| 💄    | `:lipstick:`                  | Updating the UI and style files          |
| 🎉    | `:checkered_flag:`            | Initial commit                           |
| ✅     | `:white_check_mark:`          | Adding tests                             |
| 🔒    | `:lock:`                      | Fixing security issues                   |
| 🍎    | `:apple:`                     | Fixing something on macOS                |
| 🐧    | `:penguin:`                   | Fixing something on Linux                |
| 🏁    | `:checkered_flag:`            | Fixing something on Windows              |
| 🤖    | `:robot:`                     | Fixing something on Android              |
| 🍏    | `:green_apple:`               | Fixing something on iOS                  |
| 🔖    | `:bookmark:`                  | Releasing / Version tags                 |
| 🚨    | `:rotating_light:`            | Removing linter warnings                 |
| 🚧    | `:construction:`              | Work in progress                         |
| 💚    | `:green_heart:`               | Fixing CI Build                          |
| ⬇️    | `:arrow_down:`                | Downgrading dependencies                 |
| ⬆️    | `:arrow_up:`                  | Upgrading dependencies                   |
| 📌    | `:pushpin:`                   | Pinning dependencies to specific versions |
| 👷    | `:construction_worker:`       | Adding CI build system                   |
| 📈    | `:chart_with_upwards_trend:`  | Adding analytics or tracking code        |
| ♻️    | `:recycle:`                   | Refactoring code                         |
| ➖     | `:heavy_minus_sign:`          | Removing a dependency                    |
| 🐳    | `:whale:`                     | Work about Docker                        |
| ➕     | `:heavy_plus_sign:`           | Adding a dependency                      |
| 🔧    | `:wrench:`                    | Changing configuration files             |
| 🌐    | `:globe_with_meridians:`      | Internationalization and localization    |
| ✏️    | `:pencil2:`                   | Fixing typos                             |
| 💩    | `:hankey:`                    | Writing bad code that needs to be improved |
| ⏪     | `:rewind:`                    | Reverting changes                        |
| 🔀    | `:twisted_rightwards_arrows:` | Merging branches                         |
| 📦    | `:package:`                   | Updating compiled files or packages      |
| 👽    | `::alien:`                    | Updating code due to external API changes |
| 🚚    | `:truck:`                     | Moving or renaming files                 |
| 📄    | `:page_facing_up:`            | Adding or updating license               |
| 💥    | `:boom:`                      | Introducing breaking changes             |
| 🍱    | `:bento:`                     | Adding or updating assets                |
| 👌    | `:ok_hand:`                   | Updating code due to code review changes |
| ♿️    | `:wheelchair:`                | Improving accessibility                  |
| 💡    | `:bulb:`                      | Documenting source code                  |
| 🍻    | `:beers:`                     | Writing code drunkenly                   |
| 💬    | `:speech_balloon:`            | Updating text and literals               |
| 🗃    | `:card_file_box:`             | Performing database related changes      |
| 🔊    | `:loud_sound:`                | Adding logs                              |
| 🔇    | `:mute:`                      | Removing logs                            |
| 👥    | `:busts_in_silhouette:`       | Adding contributor(s)                    |
| 🚸    | `:children_crossing:`         | Improving user experience / usability    |
| 🏗    | `:building_construction:`     | Making architectural changes             |
| 📱    | `:iphone:`                    | Working on responsive design             |
| 🤡    | `:clown_face:`                | Mocking things                           |
