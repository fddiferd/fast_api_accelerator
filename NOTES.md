
# 🚀 Quickstart



gcloud builds submit --config=cloudbuild.yaml --project wedge-golf .



## 🐍 Python Local Environment
**INITAL SETUP**
```
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```
**RUN FAST API**
```
uvicorn src.main:app --host 0.0.0.0 --port 4000 --reload
```
- test: hello world (optional - in another terminal)
```
curl http://localhost:4000/smoke-test/hello-world
```

## 🚀 Run Local Docker (Optional)
**START DOCKER**
```
shift + cmd + p 
Dev Container: Rebuild and Reopen in Container (Docker Extension in VS Code)
```
**INSTALL PYTHON REQUIREMENTS**
```
pip install -r requirements.txt
```
**RUN FAST API**
```
uvicorn src.main:app --host 0.0.0.0 --port 4000 --reload
```
- test: hello world (optional - in another terminal)
```
curl http://localhost:4000/smoke-test/hello-world
```
**BUILD DOCKER CONTAINER in GCR**
```
gcloud builds submit --config=cloudbuild.yaml --project wedge-golf-dev .
```
**RUN APPLICATION IN GCR**
```
gcloud run services replace service.yaml --region us-east1 --project wedge-golf-dev
```
**SET SERVICE POLICY IN GCR**
```
gcloud run services set-iam-policy custom-fastapi-service gcr-service-policy.yaml --region us-east1 --project wedge-golf-dev
```


# Initial Setup

## 🗄️ GCP One Time Setup
**CREATE GCP PROJECTS**
- dev
```
gcloud projects create wedge-golf-dev --name="Wedge Golf Dev"
```
- staging
```
gcloud projects create wedge-golf-staging --name="Wedge Golf Staging"
```
- prod
```
gcloud projects create wedge-golf --name="Wedge Golf"
```
**ENABLE BILLING ON ALL PROJECTS**
- dev
```

```
- staging
```

```
- prod
```

```
**PERMISSIONS FOR GITHUB**
- create service account
- add key
- add as a secret it github actions



gcloud projects add-iam-policy-binding wedge-golf-dev \
    --member=serviceAccount:git-hub-secret@wedge-golf-dev.iam.gserviceaccount.com \
    --role=roles/serviceusage.serviceUsageConsumer


gcloud projects add-iam-policy-binding wedge-golf-dev \
    --member=serviceAccount:git-hub-secret@wedge-golf-dev.iam.gserviceaccount.com \
    --role=roles/cloudbuild.builds.editor