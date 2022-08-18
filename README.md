# node-js-fetch-api
How to Make HTTP Requests in Node.js With Fetch API


```node
node --experimental-fetch your_code.js
```

```javascript
fetch('https://quotes.toscrape.com/random')
    .then((response) => response.text())
    .then((body) => {
        console.log(body);
    }); 
```

```node
node --experimental-fetch quotes.js
```

```javascript
(async () => {
    const response = await fetch('https://quotes.toscrape.com/random');
    const body = await response.text();
    console.log(body);
})();
```

```javascript
const cheerio = require("cheerio");

fetch('https://quotes.toscrape.com/random')
    .then((response) => response.text())
    .then((body) => {
        const $ = cheerio.load(body);
        console.log($('.text').text());

    })
```

```javascript
const url = 'https://httpbin.org/get'
fetch(url)
    .then(response => {
        for(const pair of response.headers){
            console.log(`${pair[0]}: ${pair[1]}`); 
          }
        return response.text();
    }).then(data => {
        console.log(data);
    });
```

```javascript
const url = 'https://httpbin.org/get';
fetch(url, {
    headers: {
        "User-Agent": "My User Agent",
    },
})
    .then((response) => response.json())
    .then(data => {
        console.log(data);
    })
```

```javascript
fetch(url, {method: “POST”})
```

```javascript
const url = 'https://httpbin.org/post'
const data = {
    x: 1920,
    y: 1080,
};
const customHeaders = {
    "Content-Type": "application/json",
}

fetch(url, {
    method: "POST",
    headers: customHeaders,
    body: JSON.stringify(data),
})
    .then((response) => response.json())
    .then((data) => {
        console.log(data);
    });
```

```javascript
fetch('https://invalid_url')
    .then((response) => response.text())
    .then((body) => {
        console.log(body);
    }).catch((error) => {
        console.error('error in execution', error);
    }); 
```

```javascript
(async () => {
    try {
        const response = await fetch('https://invalid_url');
        const body = await response.text();
        console.log(body);
    } catch (error) {
        console.error(error);
    }
})();
```

```javascript
const response = await axios.get(url);
```

```javascript
const response = await axios.post(url);
```

```javascript
const axios = require('axios');
const url = 'https://httpbin.org/post'
const data = {
    x: 1920,
    y: 1080,
};
const customHeaders = {
    "Content-Type": "application/json",
}
axios.post(url, data, {
    headers: customHeaders,
})
.then(({ data }) => {
    console.log(data);
})
.catch((error) => {
    console.error(error);
});
```

```javascript
const url = 'https://httpbin.org/post'
const data = {
    x: 1920,
    y: 1080,
};
const customHeaders = {
    "Content-Type": "application/json",
}

fetch(url, {
    method: "POST",
    headers: customHeaders,
    body: JSON.stringify(data),
})
    .then((response) => response.json())
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.error(error);
    });
```



