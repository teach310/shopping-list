# 環境構築

```Dockerfile
FROM ruby:2.7.2

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update && apt-get install -y nodejs yarn

RUN mkdir /myapp
WORKDIR /myapp
COPY Gemfile /myapp/Gemfile
COPY Gemfile.lock /myapp/Gemfile.lock
RUN bundle install

# Add a script to be executed every time the container starts.
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
```

# bootstrap
やってなかったら
$ yarn (install)

$ yarn add jquery bootstrap popper.js

```application.html.slim
```

参考
(https://yukitoku-sw.hatenablog.com/entry/2020/01/16/224422)