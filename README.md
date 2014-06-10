# docker-build

Docker build as a duplex stream. Pipe in a tar stream and pipe out the build output

``` js
npm install docker-build
```

## Usage

``` js
var build = require('docker-build')
var fs = require('fs')

fs.createReadStream('a-tar-file-with-a-dockerfile.tar')
  .pipe(build('localhost:2375'))
  .pipe(process.stdout)
```

The above example will build a docker image from the input tarball
and pipe the build output to stdout using docker running locally on port 2375.

## API

``` js
var stream = build(remote, options)
```

Where `remote` is a an address to docker - i.e. `localhost:2375` or `192.168.1.3:2375`. Defaults to `$DOCKER_HOST` or `localhost:2375`.
`options` can contain the following:

``` js
{
  tag: 'tag-the-image'
}
```


## License

MIT