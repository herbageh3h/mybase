# Scrapy

## Quick Start

- Current Version: 2.5.0, 20210801

```
pip install Scrapy
scrapy startproject helloscrapy
scrapy crawl quotes
scrapy shell 'http://quotes.toscrape.com/page/1/'
view(response) in scrapy shell

scrapy crawl quotes -O quotes.json
scrapy crawl quotes -o quotes.jl

scrapy genspider AmazonProductSpider amazon.com
```

## FAQ

### 1. How do I find xpath learning articles?

See <http://zvon.org/comp/r/tut-XPath_1.html#Pages~List_of_XPaths>.

## Scripts

```
import scrapy


class QuotesSpider(scrapy.Spider):
    name = 'quote'

    def start_requests(self):
        urls = [
            'http://quotes.toscrape.com/page/1/',
        ]
        for url in urls:
            yield scrapy.Request(url=url, callback=self.parse)

    def parse(self, response):
        for quote in response.css('div.quote'):
            yield {
                'text': quote.css('span.text::text').get(),
                'author': quote.css('small.author::text').get(),
                'tags': quote.css('div.tags a.tag::text').getall(),
            }

        next_page = response.css('li.next a::attr(href)').get()
        if next_page is not None:
            yield response.follow(next_page, callback=self.parse)
```

## Core

- scrapy.Spider
- scrapy.Request
- scrapy.Item
- start_requests(self)
- start_urls
- allowed_domains
- parse(self, response)
- response.css
- response.xpath
- response.urljoin
- response.follow
- process_item(self, item, spider)

## Response

```
response.css('title')
response.css('title::text').getall()
response.css('title::text').get()
response.css('title::text').re(r'Q\w+')
response.css('title::text').re(r'(\w+) to (\w+)')

response.xpath('//title/text()').get()
```
