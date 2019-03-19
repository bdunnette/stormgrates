# stormgrates

Basic map of Minneapolis storm grates using [CouchApp](https://github.com/couchapp/couchapp), [Leaflet](https://leafletjs.com/) and [Cloudant](https://www.ibm.com/cloud/cloudant).

Demo: https://66f2816f-a08a-4351-a05c-e237b1abe995-bluemix.cloudant.com/mpls-grates/_design/stormgrates/index.html

Source data: http://opendata.minneapolismn.gov/datasets/386fda92f6db45ddb48765259abe461c_0

Also requires a [geospatial index](https://cloud.ibm.com/docs/services/Cloudant/api?topic=cloudant-cloudant-nosql-db-geospatial#cloudant-nosql-db-geospatial) like the following:

```javascript
function (doc) {
  if (doc.geometry && doc.geometry.coordinates) {
    st_index(doc.geometry);
  }
}
```