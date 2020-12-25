# Currency Exchange Micro Service - H2

Run com.in28minutes.microservices.currencyconversionservice.CurrencyConversionServiceApplicationH2 as a Java Application.

## Resources

- http://localhost:8000/currency-exchange/from/USD/to/INR

```json
{
  "id": 10001,
  "from": "USD",
  "to": "INR",
  "conversionMultiple": 65.00,
  "environmentInfo": "NA"
}
```

## H2 Console

- http://localhost:8000/h2-console
- Use `jdbc:h2:mem:testdb` as JDBC URL


## Notes

## Tables Created
```
create table exchange_value 
(
	id bigint not null, 
	conversion_multiple decimal(19,2), 
	currency_from varchar(255), 
	currency_to varchar(255), 
	primary key (id)
)
```

## Containerization

### Troubleshooting

- Problem - Caused by: com.spotify.docker.client.shaded.javax.ws.rs.ProcessingException: java.io.IOException: No such file or directory
- Solution - Check if docker is up and running!
- Problem - Error creating the Docker image on MacOS - java.io.IOException: Cannot run program “docker-credential-osxkeychain”: error=2, No such file or directory
- Solution - https://medium.com/@dakshika/error-creating-the-docker-image-on-macos-wso2-enterprise-integrator-tooling-dfb5b537b44e

### Creating Container

- mvn package

### Running Container

#### Basic
```
docker container run --publish 8000:8000 in28min/currency-exchange:0.0.1-SNAPSHOT
```

#### To copy files
type copy file

### to share content between stages use artifacts. 
eg build stage have output that you want to share with dev stage
type publish select publish build artifacts
click add

## Azure terraform section
azure login


to create a user using command line
az ad(active directory) sp(service) create-for-rbac(role based access control) --role="Contributor" --scopes="/subscriptions/cd58d5b9-cda2-48db-971c-374db9f80bc8"

### get secure credentials
az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/cd58d5b9-cda2-48db-971c-374db9f80bc8"

#get ssh key files
ssh-keygen -m PEM -t rsa(encryption algorithm) -b 4096 (strength of the algorithm how many bits)
ssh-keygen -m PEM -t rsa -b 4096 

