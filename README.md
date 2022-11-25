

## Description of the Project

##Fetching from the API

A Single Api call is made only when the component loads for the first time .
We store States to each country using a map . And remove and append child in the State select object whenever the country is changed .

##Validating the data
The Iframe component sends data to its parent using the `Windows.Postmessage` feeature .
The Parent of receiving the message validates it using Pre-Written Javascript array of objects :

```
      const validators =[
{
    field : 'Name',
    validator : {required : true ,  minlen : 4 , maxlen : 10  }
},
{
    field : 'E-mail',
    validator : {  pattern : /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/}  // regex for email validation .
},
{
    field : 'Phone Number',
    validator : {   minlen : 10 , maxlen : 10 }
},
{
    field : 'Country',
    validator : {required : true  }
},
{
   field : 'State',
    validator : {required : true }
},

]
```
