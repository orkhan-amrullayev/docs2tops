# docs2tops stands for documents to topics.

What it basically does:
- extracts ngrams from all of the input documents
- extracts meaningful moregrams (2 or more grams) from the docs randomly sampled (sample size(0 to max) can be adjusted)
- creates semi-automated dictionary - if user provided some possible topics, docs2tops provides similar keywords for each provided topic 
- creates fully-automated and labeled dictionary.

in both cases (either user inputs some topics or not), docs2tops returns 2 dictionaries.
if user did not provide any list of topics, first dictionary will be empty with a message only.

in all cases, fully-automated dictionary will be created.

docs2tops function takes list of documents and optionally, you can provide candidate_topics_list and moregrams_sample_size.


## installation
Run the following to install:
```python
pip install docs2tops
```

## usage
```python
from docs2tops import docs2tops
import pandas as pd

df = pd.read_csv(r"C:\Users\my_file.csv")
docs = df['column_name_with_content'].to_list()

candidate_topics_list = ['smell', 'taste', 'delivery', 'packaging']
moregrams_sample_size = 100  # for maximum: len(docs) 


user_input_dict, fully_auto_dict = docs2tops(docs_input_list=docs,
              candidate_topics_list=candidate_topics_list, 
              moregrams_sample_size=moregrams_sample_size)

list_dicts = [user_input_dict, fully_auto_dict]
for result in list_dicts:
    print(result)
    print('number of topics: ', len(result))
    print('---')
```

# Developing docs2tops

to install docs2tops, along with the tools you need to develop and run tests, run the following in your virtual environment:
```bash
pip install -e .[dev]
```
