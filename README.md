The Golang Omdb API
=======
[![Build Status](https://travis-ci.org/eefret/gomdb.svg?branch=master)](https://travis-ci.org/eefret/gomdb)
[![GoDoc](https://godoc.org/github.com/eefret/go-imdb?status.svg)](https://godoc.org/github.com/eefret/go-imdb)


Author: Christopher T. Herrera (eefretsoul AT gmail DOT com)

<iframe src="http://githubbadge.appspot.com/eefret" style="border: 0;height: 142px;width: 200px;overflow: hidden;" frameBorder="0"></iframe>

This API uses the [omdbapi.com](http://omdbapi.com/) API by Brian Fritz

***
### OMDBAPI.com
This is an excellent open database for movie and film content.

I *strongly* encourage you to check it out and contribute to keep it growing.

### http://www.omdbapi.com
***
Project Usage
-------------
The API usage is very simple.

```go
package main

import (
	"fmt"
	"github.com/eefret/gomdb"
)

func main() {
	api := gomdb.Init(YOUR_API_KEY)
	
	query := &gomdb.QueryData{Title: "Macbeth", SearchType: gomdb.MovieSearch}
	res, err := api.Search(query)
	if err != nil {
		fmt.Println(err)
		return
	}
	fmt.Println(res.Search)

	query = &gomdb.QueryData{Title: "Macbeth", Year: "2015"}
	res2, err := api.MovieByTitle(query)
	if err != nil {
		fmt.Println(err)
		return
	}
	fmt.Println(res2)

	query = &gomdb.QueryData{Title: "Rick and Morty", Season: "1", Episode: "8", SearchType: gomdb.EpisodeSearch}
	res3, err := api.MovieByTitle(query)
	if err != nil {
		fmt.Println(err)
		return
	}
	fmt.Println(res3)
}

	query = &gomdb.QueryData{ImdbId: "tt2884018"}
	res4, err := api.MovieByImdbID(query)
	if err != nil {
		fmt.Println(err)
		return
	}
	fmt.Println(res4)

	query = &gomdb.QueryData{ImdbId: "tt0944947", Season: "1", Episode: "1", SearchType: gomdb.EpisodeSearch}
	res5, err := api.MovieByImdbID(query)
	if err != nil {
		fmt.Println(err)
		return
	}
	fmt.Println(res5)
```


See the project documentation to see the Response Objects and stuff
