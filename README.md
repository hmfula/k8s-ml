# k8s-ml
Purpose: To learn building, deploying and using an ML model using Docker and k8s. 

# TODO sanitize the text


# build and serve a simple ml model


# Install dependencies
`pip3 install -r requirements.txt`


# Train ML model
`python3  train_model.py`

# Build docker container. Run This in a directory containing all required files including the model.pkl
`docker build -t fast-ml .`


# Run docker container (it is launching a fastapi server with a route "/predict" which is used to access (inference) the trained ml model)
3000 port on the host,
8000,  actual port on which the server will listen at. It is the same as containerPort in k8s Deployment and targetPort in a k8s svc

`docker run -p 3000:8000 fast-ml`


# Test prediction in Docker

`curl -X POST -H 'Content-Type: application/json' -d '{"data":[5.1,3.5,1.4,0.2]}'  http://localhost:3000/predict`

{"prediction":[0]}

## Resp
{"prediction":[0]}

`curl -X POST -H 'Content-Type: application/json' -d '{"data":[5.1,3.5,5.4,5.2]}'  http://localhost:3000/predict`

## Resp

{"prediction":[2]}

## TODO complete required steps for k8s


