---
subcategory: "DNS Services"
layout: "ibm"
page_title: "IBM : dns_custom_resolver"
description: |-
  Manages IBM Private DNS Custom Resolver.
---

# ibm_dns_custom_resolver

Provides a private DNS Custom Resolver resource. This allows DNS Custom Resolver to  create, update, and delete. For more information, about Customer Resolver, see [reate-custom-resolver](https://cloud.ibm.com/apidocs/dns-svcs#create-custom-resolver).


## Example usage

```terraform
resource "ibm_dns_custom_resolver" "example" {
  name                      = "testCR-TF"
  instance_id               = "instance_id"
  description               = "new test CR TF desc"
  locations {
    subnet_crn  = "crn:v1:staging:public:is:us-south-1:a/01652b251c3ae2787110a995d8db0135::subnet:0716-03d54d71-b438-4d20-b943-76d3d2a1a590"
    enabled     = true
  }
}
```

## Argument reference
Review the argument reference that you can specify for your resource. 

- `instance_id` - (Required, string) The GUID of the private DNS service instance.
- `name`- (Required, String) The name of the custom resolver.
- `description` - (Optional, string) Descriptive text of the  custom resolver.
- `locations`- (Required, Set) The list of locations where this custom resolver is deployed. There is no update for location argument in  resolver resource.

  Nested scheme for `locations`:
  - `subnet_crn` - (Required, String) subnet crn
  - `enabled`- (Optional, Bool) Whether the location is enabled.

## Attribute reference
In addition to all argument reference list, you can access the following attribute references after your resource is created. 

- `created_on` - (Timestamp) The time (created On) of the DNS Custom Resolver. 
- `id` - (String) The unique ID of the private DNS custom resolver.
- `modified_on` - (Timestamp) The time (modified On) of the DNS Custom Resolver.
- `health`- (String) The status of DNS Custom Resolver's health. Possible values are `DEGRADED`, `CRITICAL`, `HEALTHY`.
- `locations` - (Set) Locations on which the custom resolver will be running.

  Nested scheme for `locations`:
  - `healthy`- (String) The health status.
  - `dns_server_ip`- (String) The dns server ip.
  - `enabled`- (String) Whether the location is enabled.
  - `location_id`- (String) The location id.

## Import
The `ibm_dns_custom_resolver` can be imported by using private DNS instance ID, Custom Resolver ID.
The `id` property can be formed from `custom_resolver_id` and `instance_id` in the following format:
<custom_resolver_id>:<instance_id>

**Example**

```
$ terraform import ibm_dns_custom_resolver.example 270edfad-8574-4ce0-86bf-5c158d3e38fe:345ca2c4-83bf-4c04-bb09-5d8ec4d425a8
```