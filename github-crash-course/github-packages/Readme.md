export GH_USERNAME='spB0B'
GH_IMAGE_NAME='Hello-world"
export GH_VER ='1.0.0'

echo $GH_TOKEN | docker login ghcr.io -u $GH_USERNAME --password-stdin
docker tag $GH_IMAGE_NAME:latest ghcr.io/$GH_USERNAME/$GH_IMAGE_NAME:$GH_VER

docker tag hello-world:latest ghcr.io/spb0b/hello-world:1.0.0
docker push ghcr.io/spb0b/hello-world:1.0.0