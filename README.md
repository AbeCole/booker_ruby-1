# Booker Ruby Client

Client for the Booker v4 API. See http://apidoc.booker.com for method-level documentation.

## Setup

Configuration may be specified via the environment or when initializing Booker::Client:

Configuring via environment variables:
```
BOOKER_CLIENT_ID = YOUR_CLIENT_ID
BOOKER_CLIENT_SECRET = YOUR_CLIENT_SECRET
BOOKER_BUSINESS_SERVICE_URL = https://app.secure-booker.com/webservice4/json/BusinessService.svc
BOOKER_CUSTOMER_SERVICE_URL = https://app.secure-booker.com/webservice4/json/CustomerService.svc
BOOKER_DEFAULT_PAGE_SIZE = 10
BOOKER_API_DEBUG = false # Set to true to print request details to the log
```

To ease development, **the gem points to Booker's API Sandbox at apicurrent-app.booker.ninja by default**. For production, you must specify the service urls via the environment or when initializing Booker::Client.

## Using Booker::Client

There are two client classes. **Booker::CustomerClient** is used to interact with the v4 CustomerService. **Booker::BusinessClient** is used to interact with the v4 BusinessService.

The client handles authorization and requesting new access tokens as needed.

```
# Initialize your client

business_client = Booker::BusinessClient.new(
  booker_account_name: self.booker_account_name,
  booker_username: self.booker_username,
  booker_password: self.booker_password
)

# Make requests

locations = client.find_locations

treatments = client.find_treatments(booker_location_id: locations.first.ID)
```

## Available Methods

For available methods, see:
* [common_rest.rb](lib/booker/common_rest.rb)
* [business_rest.rb](lib/booker/business_rest.rb)
* [customer_rest.rb](lib/booker/customer_rest.rb)

## Handling dates and times

ActiveSupport::TimeWithZone is a required dependency that allows the gem to seamlessly transforms timestamps from Booker's format to Ruby `Time` objects in the current `Time.zone`.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/HireFrederick/booker_ruby.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
