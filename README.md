# Crypto Notebooks

Demonstration of basic cryptographic concepts with [PyCryptodome library](https://pypi.org/project/pycryptodome/).
Examples are organized as [Jupyter Notebooks](https://jupyter.org/) and the entire runtime environment is enclosed in a 
[Docker](https://www.docker.com/) image. So you need [Docker](https://www.docker.com/) for the follwing instructions to work.

## Experiment with notebooks

Just clone project repository
```
git clone https://github.com/pzktit/CryptoNotebooks
cd CryptoNotebooks
```
Then issue
```
docker-compose up -d
```
The above will download a the required docker image and create a running container.
Then point your browser to the address [http://localhost:8888](http://localhost:8888).
You will be asked for the token. Please enter "``password``". 
Then you should see the Jupyter Lab. The ``work`` folder is mapped to the folder ``CryptoNotebooks``.
The container will be running until ShutDown a the lab (``File->ShutDown``).

## Advanced

1. You can change the password value by editing file ``docker-compose.yml`.
2. You can run the image from command line in interactive mode
   ```
    docker run --rm -ti --name cryptonotebooks \
	   -e JUPYTER_ENABLE_LAB=yes -p 8888:8888 -v ${PWD}:/home/jovyan/work pzktit/cryptonotebooks
	 ```
3. You can customize the image up to your needs. Please go to ``build_your_image`` folder, modify the ``Dockerfile`` and build 
   ```
	 docker build . --file Dockerfile --tag pleaseadapttag/toyourneeds
	 ```
