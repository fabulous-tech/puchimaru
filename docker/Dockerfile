FROM ruby:2.5.5
ENV APP_HOME /src

RUN apt-get update -qq && \
  apt-get install -y --no-install-recommends \
  build-essential \
  libpq-dev \
  nodejs && \
  apt-get clean

WORKDIR $APP_HOME
ENV BUNDLE_JOBS=4

COPY ../src/Gemfile ../src/Gemfile.lock $APP_HOME/

RUN bundle config build.nokogiri --use-system-libraries
RUN bundle install

ADD ../src /src

#EXPOSE 3000

#CMD ["bundle", "exec", "rails", "s", "-p", "3000", "-b", "0.0.0.0"]