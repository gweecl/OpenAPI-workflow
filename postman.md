## To update shared Postman documentation with OpenAPI specifications

> As of now, Postman does not support direct update of collection usinng OpenAPI specifications.

1. Import updated OAS to Postman as new collection.
1. Export it to Postman Collection v2.1 (recommended).
1. Edit the export JSON file with the main content enclosed in `collection` attribute. Refer to example in [Postman update collection API](https://documenter.getpostman.com/view/631643/JsLs/#aa3701e8-7f99-b421-7d74-0d571b051f3c).
1. Using [Postman API](https://api.getpostman.com/) or refer to the Postman collection web url, retrieve the collection id that you want to update.
1. Using [Postman API](https://api.getpostman.com/), update the collection. Example using `curl`:
  ```cli
  curl --location --request PUT 'https://api.getpostman.com/collections/{{YOUR_COLLECTION_ID}}' \
  --header 'Content-Type: application/json' \
  --header 'X-Api-Key: {{YOUR_API_KEY}}' \
  --data '@{{YOUR_UPDATED_POSTMAN_COLLECTION_IN_JSON}}'

  ```
  
## Reference
- [Postman API key](https://learning.postman.com/docs/developer/intro-api/)

