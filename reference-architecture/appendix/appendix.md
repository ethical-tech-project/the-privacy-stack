# Appendix

<br/>

## Examples of Policies

Similar to the concept of IAM policies, policies in the data privacy context can fall under several types:

**purpose-based policies:** purpose-based policies are attached to a certain purpose. For example, you can attach the policy to the **analytics** purpose, stating that all software performing actions with the analytics purpose are allowed to perform SELECT and INSERT queries on child resources tagged with Personally Identifiable Information (PII).

```
 {
  // Purposes specify the scope of purposes this policy applies to.  It can be a single string or a list of strings.
  Purposes: "analytics",

	// Resources specify the scope of resources this policy applies to. It can be a single "resource name" or a list of "resource names" or a list of ResourceFilter objects
  Resources: "srn:::table/employees/public/user_crm_data",
  Resources: ["srn:::table/employees/public/user_crm_data"],
  Resources: [
    // ResourceFilter objects specify a variety of mechanisms for searching/filtering resources. All of the "verbs" in a single ResourceFilter are "AND'd" together
    {
      // Type is a string or list of strings that specifies the resource type: catalog, database, schema, dataset, attribute, row
      Type: "dataset",
      Type: ["catalog", "database"],

      // Named is a string or list of strings that specifies the resource name either in a fully qualified "resource name" or a fully-qualified simple name
      // Note `Resources: "srn:::dataset/employees/public/user_crm_data",` is equivalent to `Resources: [{Type: "dataset", Named: "employees.public.user_crm_data"}],`
      Named: "user_crm_data",
      Named: "employees.public.user_crm_data",
      Named: "srn:::dataset/employees/public/user_crm_data",
      Named: ["user_crm_data", "employee_crm_data"],

      // Tagged is a string or list of strings or object or list of objects that specify the tags that matching resources will have. If no value is provided
      // then only "existence" is checked.
      Tagged: "financial"
      Tagged: ["financial", "pii"],
      Tagged: {
        "region": "east",
        "sensitive": true
      },
      Tagged: [
        {
          "region": ["east", "west"],
        },
        "pii"
      ],
    },

    // Additional ResourceFilters may be specified and they are "OR'd"
  ],

	// Constraints specify the scope of additional attributes
  Constraints: [
    {
      "StringEquals": {
        "principal.country": "US"
      },
      "DateLessThan": {
        "currentTime": "2021-04-01"
      }
    }
  ]

  // Effects specify the effects applied after a scope matches.
  Effects: [
    {
      // Grant is either "allow" (default) or "deny".
      Grant: "allow",

      // Constrain to attributes
      Type: "attribute",

      // Constrain to child resources tagged with "pii"
      Tagged: "pii",

      // Actions are the actions that are granted
      Actions: ["SELECT", "INSERT"],

      // Obligation is a URI reference to an obligation that a technical operator can then map to technical actions
      Obligation: "<http://ketch.com/v1.0/tokenize>",

			// Condition is a filter to apply to the data
      Condition: "attr > value"

			// Consent is a row-level condition to apply to the data. It can be a single string or list of strings.
			Consent: "analytics"
			Consent: ["analytics", "retargeting"]
    },
  ]

}
```

<br/>

**principal-based policies:** principal-based policies, which are analogous to identity-based policies in AWS, are attached to a particular user identity, group, or role. These policies let you specify what the identity can do. For example, you can attach the policy to the **analysts** role, stating that all analysts are allowed to run queries on the `user_crm_data`.


```
 {

  // Principals specify the scope of principals this policy applies to. It can be a single "principal name" or a list of "principal names"
  Principals: "srn:::group/analysts",

  // Resources specify the scope of resources this policy applies to. It can be a single "resource name" or a list of "resource names" or a list of ResourceFilter objects
  Resources: "srn:::table/employees/public/user_crm_data",
  Resources: ["srn:::table/employees/public/user_crm_data"],
  Resources: [
    // ResourceFilter objects specify a variety of mechanisms for searching/filtering resources. All of the "verbs" in a single ResourceFilter are "AND'd" together
    {
      // Type is a string or list of strings that specifies the resource type: catalog, database, schema, dataset, attribute, row
      Type: "dataset",

      // Named is a string or list of strings that specifies the resource name either in a fully qualified "resource name" or a fully-qualified simple name
      // Note `Resources: "srn:::dataset/employees/public/user_crm_data",` is equivalent to `Resources: [{Type: "dataset", Named: "employees.public.user_crm_data"}],`
      Named: "srn:::table/employees/public/user_crm_data",

      // Tagged is a string or list of strings or object or list of objects that specify the tags that matching resources will have. If no value is provided
      // then only "existence" is checked.
      Tagged: ["financial", "pii"],
    },

    // Additional ResourceFilters may be specified and they are "OR'd"
  ],

	  // Constraints specify the scope of additional attributes
  Constraints: [
    {
      "StringEquals": {
        "principal.country": "US"
      },
      "DateLessThan": {
        "currentTime": "2021-04-01"
      }
    }
  ]

  // Effects specify the effects applied after a scope matches.
  // Each Effect extends ResourceFilter to constrain the effect to a child
  // resource of one of the Resources scopes.
  Effects: [
    {
      // Grant is either "allow" (default) or "deny".
      Grant: "allow",

      // Constrain to attributes
      Type: "attribute",

      // Constrain to child resources tagged with "pii"
      Tagged: "pii",

      // Actions are the actions that are granted
      Actions: ["SELECT", "INSERT"],

      // Obligation is a URI reference to an obligation that a technical operator can then map to technical actions
      Obligation: "<http://ketch.com/v1.0/tokenize>",

			// Condition is a filter to apply to the data
      Condition: "attr > value"

			// Consent is a row-level condition to apply to the data. It can be a single string or list of strings.
			Consent: "analytics"
			Consent: ["analytics", "retargeting"]
    },
  ]

}
```
<br/>

**resource-based policies:** resource-based policies are attached to a resource. For example, you can attach resource-based policies to the table `user_crm_data`. With resource-based policies, you can specify who has access to the resource and which actions they can perform.


```
{

  // Resources specify the scope of resources this policy applies to. It can be a single "resource name" or a list of "resource names" or a list of ResourceFilter objects
  Resources: "srn:::table/employees/public/user_crm_data",
  Resources: ["srn:::table/employees/public/user_crm_data"],
  Resources: [
    // ResourceFilter objects specify a variety of mechanisms for searching/filtering resources. All of the "verbs" in a single ResourceFilter are "AND'd" together
    {
      // Type is a string or list of strings that specifies the resource type: catalog, database, schema, dataset, attribute, row
      Type: "dataset",
      Type: ["catalog", "database"],

      // Named is a string or list of strings that specifies the resource name either in a fully qualified "resource name" or a fully-qualified simple name
      // Note `Resources: "srn:::dataset/employees/public/user_crm_data",` is equivalent to `Resources: [{Type: "dataset", Named: "employees.public.user_crm_data"}],`
      Named: "user_crm_data",
      Named: "employees.public.user_crm_data",
      Named: "srn:::dataset/employees/public/user_crm_data",
      Named: ["user_crm_data", "employee_crm_data"],

      // Tagged is a string or list of strings or object or list of objects that specify the tags that matching resources will have. If no value is provided
      // then only "existence" is checked.
      Tagged: "financial"
      Tagged: ["financial", "pii"],
      Tagged: {
        "region": "east",
        "sensitive": true
      },
      Tagged: [
        {
          "region": ["east", "west"],
        },
        "pii"
      ],
    },

    // Additional ResourceFilters may be specified and they are "OR'd"
  ],

	  // Constraints specify the scope of additional attributes
  Constraints: [
    {
      "StringEquals": {
        "principal.country": "US"
      },
      "DateLessThan": {
        "currentTime": "2021-04-01"
      }
    }
  ]

  // Effects specify the effects applied after a scope matches.
  // Each Effect extends ResourceFilter to constrain the effect to a child
  // resource of one of the Resources scopes.
  Effects: [
    {
      // Grant is either "allow" (default) or "deny".
      Grant: "allow",

      // Constrain to attributes
      Type: "attribute",

      // Constrain to child resources tagged with "pii"
      Tagged: "pii",

      // Actions are the actions that are granted
      Actions: ["SELECT", "INSERT"],

      // Obligation is a URI reference to an obligation that a technical operator can then map to technical actions
      Obligation: "<http://ketch.com/v1.0/tokenize>",

			// Condition is a filter to apply to the data
      Condition: "attr > value"

			// Consent is a row-level condition to apply to the data. It can be a single string or list of strings.
			Consent: "analytics"
			Consent: ["analytics", "retargeting"]
    },
  ]

}
```

