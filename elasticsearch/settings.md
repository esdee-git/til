updating es 5.x.x settings to add new analyzer will not work if 'mappings' section exists in the query json

for example, this will not work:

{
  "settings": {
    "analysis": {
      "filter": {
        "custom_english_stemmer": {
          "type": "stemmer",
          "name": "english"
        }
      },
      "analyzer": {
        "custom_lowercase_stemmed": {
          "tokenizer": "standard",
          "filter": [
            "lowercase",
            "custom_english_stemmer"
          ]
        }
      }
    }
  },
  "mappings": {
    "docs": {
      "properties": {
        "text": {
          "type": "string",
          "analyzer": "custom_lowercase_stemmed"
        }
      }
    }
  }
}

it errupts
{
  "error" : {
    "root_cause" : [
      {
        "type" : "illegal_argument_exception",
        "reason" : "Can't update non dynamic settings [[index.analysis.analyzer.custom_lowercase_stemmed.filter.0, index.analysis.analyzer.custom_lowercase_stemmed.filter.1, index.analysis.analyzer.custom_lowercase_stemmed.tokenizer, index.analysis.filter.custom_english_stemmer.name, index.analysis.filter.custom_english_stemmer.type]] for open indices [[number_test/-god6mu5Qveds0eb6ZOScA]]"
      }
    ],
    "type" : "illegal_argument_exception",
    "reason" : "Can't update non dynamic settings [[index.analysis.analyzer.custom_lowercase_stemmed.filter.0, index.analysis.analyzer.custom_lowercase_stemmed.filter.1, index.analysis.analyzer.custom_lowercase_stemmed.tokenizer, index.analysis.filter.custom_english_stemmer.name, index.analysis.filter.custom_english_stemmer.type]] for open indices [[number_test/-god6mu5Qveds0eb6ZOScA]]"
  },
  "status" : 400
}

while this works:
{
  "settings": {
    "analysis": {
      "filter": {
        "custom_english_stemmer": {
          "type": "stemmer",
          "name": "english"
        }
      },
      "analyzer": {
        "custom_lowercase_stemmed": {
          "tokenizer": "standard",
          "filter": [
            "lowercase",
            "custom_english_stemmer"
          ]
        }
      }
    }
  }
}

