# snowplow
Schema files are formatted as JSON schema describing your custom attributes known as an iglu file in the Snowplow documentation.

Follow the below structure for specifying schemas
> schemas/{app_id}/.../{event_name}/jsonschema/{version}.json

```
schemas
├── app_id                          // unique identifer for the service/app
    ├── event_name                  // name of the event to be tracked
        ├── jsonschema      
            ├── version.json        // event version
```

## Steps to create a new schema
1. Write a JSONSchema file describing your custom event and store it as per above folder structure
2. [Validate](https://jsonschemalint.com/) your schema for syntax issues
3. Each schema file has a mandatory **'title'** that should match the event name.
4. Use the URL that you established in step 1 as the schema URL when you call Snowplow:
```javascript
window[snowplowName]('trackPageView', null, [{
schema: 'https://raw.githubusercontent.com/fivetran/snowplow-schemas/master/1-0-0.json',
data: {
hello: 'Hello world!',
hello_array: ['Hello', 'world!']
}
}]);
```

