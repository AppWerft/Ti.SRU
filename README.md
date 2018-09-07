# Ti.SRU

This is the Titanium/Axway module for connecting with SRU service.

SRU (Search/Retrieve via URL) is a standard search protocol for Internet search queries, utilizing CQL (Common Query Language) and standard query syntax for representing queries.

In the context of libraries, SRU is mainly used for search and retrieval of bibliographic records from the catalog.


## How to use

After installing of module in your app you can use the module with the code below:

```
const SRU = require('ti.sru');
const Endpoint = SRU.createEndpoint({
	url: YOUR_URL, 
	version : '1.2',  // default
	accesstoken : 'ABCDEFGHJKL' // optional
});
```

### Explain operation

The explain operation allows a client to retrieve a description of the facilities available at an SRU server. It can then be used by the client to self-configure and provide an appropriate interface to the user:

The response includes list of all the searchable indexes. These are the indexes that are configured by the institution. They can be used for the searchRetrieve operation. Sortable indexes have a "sort=true" indication.
Note that each institution might configure a different set of indexes.

```
Endpoint.explain(function(res){
	console.log(res);
})
```

An typical answer is [here](https://na01.alma.exlibrisgroup.com/view/sru/TR_INTEGRATION_INST?version=1.2&operation=explain). The format of the example response is XML, this module method answers in format JSON.
 
### SearchRetrieve operation