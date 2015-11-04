UK House Price paid elasticsearch import
========================================



This is a logstash config which will parse the `CSV` file provided by the UK Government into the correct fields and insert into ElasticSearch. You need to download the data set from the UK Government open data site [here][download_page], a link to the full 3.5GB `CSV` is [here][single_file]. A detail about the meaning of the various column headings is also on their [site][column_headings].

Running
-------

You should be able to simply run `run.sh` after modifying the `logstash.conf` to point to your downloaded `CSV` file and to your Elastic Search instance.

Example imported data
---------------------

Once the data is imported the fields you can expect are as below.

    {
              "message" => [
            [0] "\"{21E5FEB7-A660-2439-E050-A8C06205342E}\",\"220000\",\"2012-02-23 00:00\",\"CV31 3NE\",\"D\",\"N\",\"F\",\"5A\",\"\",\"SPENCER STREET\",\"\",\"LEAMINGTON SPA\",\"WARWICK\",\"WARWICKSHIRE\",\"B\",\"A\"\r"
        ],
             "@version" => "1",
           "@timestamp" => "2015-11-04T11:53:22.273Z",
                 "uuid" => "{21E5FEB7-A660-2439-E050-A8C06205342E}",
                "price" => "220000",
        "original_date" => "2012-02-23 00:00",
             "postcode" => "CV31 3NE",
        "property_type" => "D",
              "old/new" => "N",
             "duration" => "F",
                 "paon" => "5A",
               "street" => "",
             "locality" => "SPENCER STREET",
            "town/city" => "",
             "district" => "LEAMINGTON SPA",
               "county" => "WARWICK",
         "ppd_category" => "WARWICKSHIRE",
        "record_status" => "B",
             "column16" => "A"
    }


I did this so I could play with a reasonable dataset in Elastic Search, and put it up on GitHub so I don't need to re-create the config if I ever want the dataset again. If you find it useful in any way that makes me happy.


[single_file]: http://publicdata.landregistry.gov.uk/market-trend-data/price-paid-data/b/pp-complete.txt
[download_page]: https://www.gov.uk/government/statistical-data-sets/price-paid-data-downloads
[column_headings]: https://www.gov.uk/guidance/about-the-price-paid-data#explanation-headings
