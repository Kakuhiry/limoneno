FROM --platform=linux/x86-64 ruby:2.6.3
WORKDIR /app
COPY ./ ./
RUN apt-get update -y
RUN apt-get install -y nano default-mysql-client libnetcdf-dev libssl-dev libcrypto++-dev libgmp-dev
RUN bundle config set deployment 'true'
RUN gem install mysql2 sequel sqlite3 bundler foreman
RUN bundle install
RUN chmod +x start.sh
ENTRYPOINT ["sh", "start.sh"]
