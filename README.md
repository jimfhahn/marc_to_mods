## README for `marc_to_mods`

This is a set of Dockerized scripts to convert Library of Congress MarcXML to MODS.

### Usage

1. Spin up the container.

```bash
docker-compose up -d
```

2. Copy the XML into the container.

```bash 
docker cp /var/hold/BooksAll.2014*.xml $CONTAINER_ID:/var/local/.
```

3. Install `xsltproc`. (TODO: integrate with XSLT Docker image to eliminate this step.

```bash
docker exec $CONTAINER_ID apt-get update && apt-get install xsltproc
```

4. Run the scripts.  This will take a while, a screen or tmux session is recommend.

```bash
docker exec -it $CONTAINER_ID bash -c "./usr/local/sbin/Split_MARCXML_file.sh /var/local/BooksAll.2014*.xml 500"
```

### License

This code is available as open source under the terms of the [Apache 2.0 License](https://opensource.org/licenses/Apache-2.0).
