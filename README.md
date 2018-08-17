A simple attempt to recreate an error seen in another project

Steps followed:

```
cd aws_sdk_test
gem install rails
rails new .
```
edit Gemfile to add `gem 'aws-sdk', '~> 2'`
`bundle install`
create new initializer
```
# config/initializers/aws.rb
Aws.config.update({
  region: 'us-east-1',
  credentials: Aws::Credentials.new(ENV['AWS_ACCESS_KEY_ID'], ENV['AWS_SECRET_ACCESS_KEY']),
})

S3_BUCKET = Aws::S3::Resource.new.bucket(ENV['S3_BUCKET'])
```
Start up the console
`S3_BUCKET=XXX AWS_ACCESS_KEY_ID=XXX AWS_SECRET_ACCESS_KEY=XXX rails c`
everything is fine

Update gemfile:
`gem 'aws-sdk', '~> 3'`
`bundle install`
Start up the console
`S3_BUCKET=XXX AWS_ACCESS_KEY_ID=XXX AWS_SECRET_ACCESS_KEY=XXX rails c`

Failure
