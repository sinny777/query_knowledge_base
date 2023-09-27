# WIP on Enterprise Search using different techniques

Please NOTE that this is currently WIP

## Prerequisites (Environment):

```

#FOR MAC OS
export HNSWLIB_NO_NATIVE=1

pyenv install 3.10.2
pyenv global 3.10.2

pip install --upgrade pip
pip install virtualenv

virtualenv venv -p python3.10.2
source venv/bin/activate

<!-- pip freeze > requirements.txt
pip install -r requirements.txt -->

```

  - **Or you can install following libraries separately as well**

```

pip install python-dotenv
pip install "ibm-watson-machine-learning>=1.0.320" | tail -n 1
pip install "pydantic>=1.10.0" | tail -n 1
pip install langchain | tail -n 1
pip install langchain --upgrade
pip install PyPDF2

pip install "unstructured[pdf]"
pip install chromadb
pip install chroma-migrate

pip install llama-index llama_hub wikipedia
pip install llama-cpp-python


pip install pypdf
pip install InstructorEmbedding
pip install 'transformers[torch]'
pip install sentence-transformers
pip install Flask flask-restful flask_httpauth
pip install cachetools
pip install unstructured
pip install from-root
pip install text-extensions-for-pandas
pip install --upgrade ibm-watson
pip install jupyterlab
pip install matplotlib

NOT REQUIRED
pip install primeqa
pip install faiss-cpu
pip install ibm-generative-ai
pip install "ibm-generative-ai[langchain]"

```

### Make sure you have ".env" file with the content as in env_example file

```

LOGLEVEL=DEBUG

WD_API_KEY=<REPLACE_WITH_YOUR_WATSON_DISCOVERY_API_KEY>
WD_ENDPOINT=<REPLACE_WITH_YOUR_WATSON_DISCOVERY_ENDPOINT>
WD_PROJECT_ID=<REPLACE_WITH_YOUR_WATSON_DISCOVERY_PROJECT_ID>

IBM_CLOUD_API_KEY=<REPLACE_WITH_YOUR_IBM_CLOUD_API_KEY>
WATSONX_AI_ENDPOINT=<REPLACE_WITH_YOUR_WATSONX_AI_ENDPOINT>
WX_PROJECT_ID=<REPLACE_WITH_YOUR_WATSONX_PROJECT_ID>


```

### Make sure you have created following folders at root

  - datasets
  - datasets/splits

Place the PDF file inside datasets (innovation-onepagers-ibm.pdf)

```

LOGLEVEL=DEBUG

WD_API_KEY=<REPLACE_WITH_YOUR_WATSON_DISCOVERY_API_KEY>
WD_ENDPOINT=<REPLACE_WITH_YOUR_WATSON_DISCOVERY_ENDPOINT>
WD_PROJECT_ID=<REPLACE_WITH_YOUR_WATSON_DISCOVERY_PROJECT_ID>

IBM_CLOUD_API_KEY=<REPLACE_WITH_YOUR_IBM_CLOUD_API_KEY>
WATSONX_AI_ENDPOINT=<REPLACE_WITH_YOUR_WATSONX_AI_ENDPOINT>
WX_PROJECT_ID=<REPLACE_WITH_YOUR_WATSONX_PROJECT_ID>


```

### START Jupyter Lab

```
source venv/bin/activate
jupyter lab

```


## REFERENCES:

  - [Watsonx.ai - Platform](https://dataplatform.cloud.ibm.com/wx/home?context=wx)
  - [IBM Watson Discovery Documentation](https://cloud.ibm.com/docs/discovery-data?topic=discovery-data-upload-data)
  - [IBM Watson Discovery V2 API](https://cloud.ibm.com/apidocs/discovery-data#adddocument)
  - [Article on WD Enrichments](https://community.ibm.com/community/user/ai-datascience/blogs/bill-murdock1/2022/01/14/enriching-your-documents-can-make-search-more-effe)
  - [Running IBM Watson NLP locally](https://heidloff.net/article/running-ibm-watson-nlp-locally-in-containers/)
  - [RAG Article](https://medium.com/towards-generative-ai/superknowa-simplest-framework-yet-to-swiftly-build-enterprise-rag-solutions-at-scale-ca90b49be28a)
  - [Deploy Watson NLP model to CP4D](https://medium.com/@alex.lang/deploy-watson-nlp-models-in-ibm-cloud-pak-for-data-f16b4d8b0cc7)
  - [Watson NLP Embed Documentation](https://www.ibm.com/docs/en/watson-libraries?topic=models-creating-custom)
  
