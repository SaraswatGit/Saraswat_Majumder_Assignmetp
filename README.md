

## Description of the Project

## Fetching from the API

A Single Api call is made only when the component loads for the first time .
We store States to each country using a map . And remove and append child in the State select object whenever the country is changed .

```
const countryStatemap={};  // each country will be mapped to its states 
        fetch('https://raw.githubusercontent.com/stefanbinder/countries-states/master/countries.json')
            .then(response => response.json())
            .then(country_list => {
                let i = 0;
                for (; i < country_list.length; i++) {
                    const options = document.createElement("option");
                    options.innerText = country_list[i].name;
                    options.setAttribute("value", `${country_list[i].code3}`)
                    country.appendChild(options);
                    const statesList = country_list[i].states;
                    countryStatemap[country_list[i].code3]=statesList;

                }

            })
            .catch(error => console.error(error));
```

## Validating the data
The Iframe component sends data to its parent using the `Windows.Postmessage` feature  : 
eg : 
```   
 window.parent.postMessage(JSON.stringify(formvalues), "*");
```

The Parent of the iframe validates it using Pre-Written Javascript array of objects :

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
## How to run the project : 
1)You can download and extract the zip
2)Copy the file path . 
3)Paste the file path on the browser seach bar and hit enter . 
