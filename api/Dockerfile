FROM ruby:2.7

ENV LANG=C.UTF-8 \
  TZ=Asia/Tokyo

# dockerの作業ディレクトリの指定
WORKDIR /myapp
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client
COPY Gemfile /myapp/Gemfile
COPY Gemfile.lock /myapp/Gemfile.lock
RUN bundle install

# Add a script to be executed every time the container starts.
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]