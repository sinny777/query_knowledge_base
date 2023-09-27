## WIP on Enterprise Search using different techniques

Please NOTE that this is currently WIP

### Prerequisites:

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

### Make sure you have ".env" file with following content

```

LOGLEVEL=DEBUG

GENAI_KEY=pak-<REPLACE IT WITH YOUR IBM GENAI APIKEY>
GENAI_API=<REPLACE IT WITH YOUR IBM GENAI ENDPOINT>

REST_USERNAME=admin
REST_PASSWORD=1SatnamW
DATA_PATH=./datasets


```

### START THE API SERVER

```
source venv/bin/activate
python app/main.py

```

###  RUN AS DOCKER CONTAINER

```

docker run --rm -it --name watsonx  \
--privileged \
-v /tmp:/tmp \
-p 8080:8080 \
--env-file .env \
sinny777/watsonx:latest

docker run --rm -it --name watsonx  \
-v /tmp:/tmp \
-p 8080:8080 \
--env-file .env \
sinny777/watsonx:latest

```

  - Now you can use REST endpoint to summarize or RAG way of using LLMs
  - Check the docs/REST.md file for reference



# DEPLOY TO IBM CLOUD CODE_ENGINE

```


ibmcloud login --sso

ibmcloud ce project select --name RetailDemo

ibmcloud ce secret create --name watsonx-secrets --from-env-file .env
ibmcloud ce app create --name watsonx-demo --image docker.io/sinny777/watsonx:latest --env-from-secret watsonx-secrets

ibmcloud ce app create --name watsonx-demo --image docker.io/sinny777/watsonx:latest --min-scale 1 --env-from-secret watsonx-secrets --port 8080 --memory 4G --cpu 1 --nw

ibmcloud ce application events -n watsonx-demo
ibmcloud ce app events --app watsonx-demo
ibmcloud ce application logs -f -n watsonx-demo
ibmcloud ce app events --instance watsonx-demo-00001-deployment-68bc59fcb4-ftv59



```

## Deploy it on a VM

```

ssh root@52.116.51.123

cd watsonx/watsonx
source venv/bin/activate

python app/main.py


lsof -t -i:8080
sudo kill -9 6279

sudo kill -9 $(sudo lsof -t -i:8080)

```

## REFERENCES:

  - [Watsonx.ai - Developer](https://bam.res.ibm.com)
  - [IBM Foundation Model - BumPy](https://github.ibm.com/ai-foundation/bampy)
  - [Running IBM Watson NLP locally](https://heidloff.net/article/running-ibm-watson-nlp-locally-in-containers/)
  - [Entitlement Key](https://myibm.ibm.com/products-services/containerlibrary)
  - [Deploy Watson NLP model to CP4D](https://medium.com/@alex.lang/deploy-watson-nlp-models-in-ibm-cloud-pak-for-data-f16b4d8b0cc7)
  - [Watson NLP Embed Documentation](https://www.ibm.com/docs/en/watson-libraries?topic=models-creating-custom)
  
