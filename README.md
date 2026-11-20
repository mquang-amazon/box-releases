# box-releases

Prebuilt binaries.

Each release has one archive per platform and a `SHA256SUMS.txt`.

## Verify

```sh
grep " <archive>$" SHA256SUMS.txt | sha256sum -c -
```

## License

See LICENSE.
