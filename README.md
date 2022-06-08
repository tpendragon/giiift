# GIIIFt

The idea behind GIIIFt is that you can add this app to a Github repository and
when you commit an image to the repository it will convert it to a IIIF image
API and provide an endpoint to automatically create a IIIF presentation 3
manifest.

## Implementation Details

Create a Github App
On Commit, send a webhook to a Lambda (which is in this repository) to notify it
that there's a new file, which will trigger creation of a pyramidal tiff. This
pyramidal tiff will either be put in Github (possible?) via a commit, or store
it in S3 paid for by Princeton or the IIIF consortium (preferred.)

That pyramidal tiff will be served by a hosted
[serverless-iiif](https://github.com/samvera-labs/serverless-iiif) file. We
could use Level 1 and just pre-generate all the files and commit it, but I think
it would be a good service to provide real level 2 resources.

For each directory of images in the repository there will be a hosted path for
converting a git tree into a presentation manifest. Or maybe when a new commit
is added it'll generate the manifest and commit it? Might be more reliable and
less expensive/complicated.

## Other Ideas

Perhaps we can implement Change Discovery on top of the git commit log?

Perhaps we can allow annotations in a separate file and provide rudimentary IIIF
search?

## Useful References

- http://www.levibotelho.com/development/commit-a-file-with-the-github-api/
