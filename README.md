# tagoquery
tagoquery : simple goquery wrapper

WIP

## Usage

### get github trending

```go
const url = "https://github.com/trending"

// Repos is represents a GitHub repostry in https://github.com/trending
type Repos struct {
	Repo []struct {
		Name        string `html:"div:nth-child(1) h3 a text{}"`
		URL         string `html:"div:nth-child(1) h3 a href{}"`
		Description string `html:"div:nth-child(3) p text{}"`
		Lang        string `html:"div:nth-child(4) span:nth-child(2) text{}"`
	} `html:"div.columns div.explore-content ol li"`
}
```

```go
// fetch repos
result := Repos{}
tagoquery.Unmarshal(url, &result)

// show repos
for i, r := range result.Repo {
  fmt.Printf("%s: %s\n", r.Name, r.URL)
}
```
