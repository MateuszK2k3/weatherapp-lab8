# weatherapp-lab8

## Opis projektu

Aplikacja pokazująca pogodę w dowolnym mieście na świecie

![app1](images/app-1.png)
![app2](images/app-2.png)

---

# Część obowiązkowa


## Instrukcja użytkowania

### a.

Aby zbudować obraz kontenera, należy użyć poniższego polecenia:

```bash
docker build -t weatherapp-lab8 .
```
![docker_build](images/build.png)

### b. 

aby uruchomić kontener na podstawie zbudowanego obrazu należy użyć polecenia:

```bash
docker run -d --rm --name weatherapp-lab8 -p 8000:8000 -e API_KEY=92d16d3db25a11ddce1f22ba69b079c3 weatherapp-lab8:latest
```
![docker_run](images/run.png)

### c. 

aby uzyskać logi należy użyć polecenia:

```bash
docker logs weatherapp-lab8
```
![docker_logs](images/logs.png)

### d. 

aby sprawdzić warstwy i rozmiar obrazu należy użyć polecenia:

```bash
docker image inspect weatherapp-lab8
```
warstwy
![docker_inspect](images/layers.png)

rozmiar
![docker_inspect](images/size.png)


# Część obowiązkowa

### Budowanie obrazu z cache i eksportem do rejestru

```bash
docker buildx build \
  --builder mybuilder \
  --platform linux/amd64,linux/arm64 \
  --tag mateuszkozz/weatherapp-lab8:v1 \
  --push \
  --cache-to=type=registry,ref=mateuszkozz/weatherapp-lab8:buildcache,mode=max \
  --cache-from=type=registry,ref=mateuszkozz/weatherapp-lab8:buildcache \
```
Deklaracja znaduje się poniżej i pokazuje, że obraz jest dostępny dla dwóch platform. Zastosowany został builder ze sterownikiem docker-container
![architectures](images/milti-platform.png)
![architectures](images/cache.png)

