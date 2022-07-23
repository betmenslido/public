# wkhtmltopdf+Alpine (walp) playground

Versions used:

| App/Lib     | Version |
| ----------- | ------- |
| alpine      | 3.15    |
| wkhtmltopdf | 0.12.6  |

## Build

`docker build . -t walp:latest`

## Run

Convert included example HTML/CSS projects into PDF. By default, image uses `/workdir/index.html` as an input, and produces `/workdir/output.pdf` as a result.

```bash
docker run --rm --mount type=bind,source="$(pwd)"/example-simple,target=/workdir walp:latest # OR
docker run --rm --mount type=bind,source="$(pwd)"/example-complex,target=/workdir walp:latest # OR
docker run --rm --mount type=bind,source="$(pwd)"/example-complex2,target=/workdir walp:latest
```

## Custom run

```
docker run --rm -it --mount type=bind,source="$(pwd)"/example-complex,target=/workdir walp:latest /bin/wkhtmltopdf --enable-local-file-access /workdir/index.html /workdir/output.pdf
```

`--enable-local-file-access` MUST be enabled to access files other than passed input HTML file. Otherwise we get:

>Warning: Blocked access to file /workdir/styles/main.css
>
>Warning: Blocked access to file /workdir/pics/cake184.jpg
