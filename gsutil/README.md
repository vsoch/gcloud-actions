# GitHub Action for Gsutil

The GitHub Actions for [gsutil](https://cloud.google.com/storage/docs/gsutil) are provided here.

## Usage

An example workflow to list the contents of a bucket:

```
workflow "Run gsutil command" {
  on = "push"
  resolves = "List Bucket"
}

action "GCP Authenticate" {
  uses = "actions/gcloud/auth@master"
  secrets = ["GCLOUD_AUTH"]
}

action "List Bucket" {
  needs = ["GCP Authenticate"]
  uses = "actions/gcloud/gsutil@master"
  env = {
    GOOGLE_BUCKET  = "the-best-bucket"
  }
  args = "ls gs://${GOOGLE_BUCKET}"
}
```

For more information about the authentication step, [see `auth`](/auth).

## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE).

Container images built with this project include third party materials. See [THIRD_PARTY_NOTICE.md](THIRD_PARTY_NOTICE.md) for details.
