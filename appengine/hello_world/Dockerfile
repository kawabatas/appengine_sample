FROM ruby:2.5.1

ENV APP_HOME /home/app
ENV BUNDLE_PATH /bundle
ENV BUNDLE_APP_CONFIG $BUNDLE_PATH
ENV PATH ${BUNDLE_PATH}/bin:$PATH

WORKDIR $APP_HOME

RUN apt-get update -qq && apt-get install -y --no-install-recommends \
      build-essential && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    gem install bundler

COPY Gemfile* ./
RUN bundle install

COPY . .
EXPOSE 8080
CMD ["bundle", "exec", "ruby", "app.rb"]
