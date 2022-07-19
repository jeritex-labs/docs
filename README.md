<p align="center">
  <img src="source/images/logo.png" alt="Slate: API Documentation Generator" width="226">
  <br>
</p>

<p align="center">Jeritex API Docs Generator</p>

This generator using Slate, check it
<https://github.com/slatedocs/slate/wiki>

# How to dev

## Generate

```bash
docker run --rm --name slate -v $(pwd)/build:/srv/slate/build -v $(pwd)/source:/srv/slate/source slatedocs/slate build
```

## Running

```bash
docker run --rm --name slate -p 4567:4567 -v $(pwd)/source:/srv/slate/source slatedocs/slate serve
```
