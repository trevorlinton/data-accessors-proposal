## Data Accessors Proposal

## Overview of Channges

* Introduces `data` property that contains a json-path-hashed-URI that can only be valid on void elements and template elements
* For void elements the `.value` property is populated with the evaluated contents as a string of the json-path-hashed-URI contained in `data` property
* For template tags with a `data` property the contents of the template tag replace the template tag with the evaluated `json-path-hashed-uri-template-resolution.
* 

### Defintion of `json-path-hashed-URI`:

A json-path-hashed-URI is a valid URI as defined by RFCXXXX that optionally may contain a hash where the hash value contains the json path as defined by RFCXXXX. 


### Definition of `json-path-hashed-uri-template-resolution`:

This is a process of evaluated a template to render it into HTML by:

1. Evaluate the `json-path-hashed-URI` as defined above. 
2. If the returned value is an array, the template's html is placed tha


## Assumptions

* Data property is not being used "officially"
* URI stored in data property returns JSON
* Authentication is not part of this scope, the request to the URI is the same as if a user had used fetch

### Example

For `https://api.example.com/user` end point, assume:

```
{
  "id":1,
  "name":"Trevor Linton,
}
```

For `https://api.example.com/user` end point, assume:

```
{
  "id":1,
  "name":"Trevor Linton,
}
```


```
<h2>User</h2>
<p data="https://api.example.com/user/#$.name">Loading...</p>
<hr/>
<form method="post" path="/user">
  <input type="text" name="name" data="https://api.example.com/user/#$.name"/>
  <input type="hidden" name="id" data="https://api.example.com/user/#$.id"/>
</form>
```

```
<h2>Users</h2>
<ul>
  <template data="https://api.example.com/users">
    <li data="https://api.example.com/users#$.[*]">
      <span class="name" data="https://api.example.com/users#$.[*].name">Loading...</span>
    </li>
  </template>
</ul>
```


