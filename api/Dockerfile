FROM ruby:2.7

ENV LANG=C.UTF-8 \
  TZ=Asia/Tokyo

# dockerの作業ディレクトリの指定
WORKDIR /app
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client
COPY Gemfile /app/Gemfile
COPY Gemfile.lock /app/Gemfile.lock
RUN bundle install

# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]