# Go SDK guidance

This independent repository is module `github.com/gethisend/hisend-go`. Use the
Go version in `go.mod`. `client.go` contains HTTP/auth configuration; resource
files implement emails, domains, routing and threads; `models.go` holds JSON
contracts; `webhooks.go` handles callback verification.

Run `go test ./...` and `go vet ./...`; format touched source with `gofmt`.
`client_test.go` uses `httptest` and overrides `BaseURL`: use this pattern for
new tests rather than the default live service.

Preserve exported API compatibility, JSON names/optional fields, HTTP error and
response handling, and webhook checks. Cross-check changed endpoints/contracts
with `../backend` and `../docs` when available. Avoid new runtime dependencies
without a clear need. Do not send live email, log secrets, tag releases, or
publish unless requested.
