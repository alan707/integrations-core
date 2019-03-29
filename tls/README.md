# Agent Check: TLS

## Overview

This check monitors [TLS][1] protocol version, certificate expiration & validity, etc.

## Setup

### Installation

The TLS check is included in the [Datadog Agent][2] package.
No additional installation is needed on your server.

### Configuration

1. Edit the `tls.d/conf.yaml` file, in the `conf.d/` folder at the root of your Agent's configuration directory to start collecting your TLS data. See the [sample tls.d/conf.yaml][2] for all available configuration options.

2. [Restart the Agent][3].

### Validation

[Run the Agent's status subcommand][4] and look for `tls` under the Checks section.

## Data Collected

### Metrics

See [metadata.csv][5] for a list of metrics provided by this integration.

### Service Checks

**`tls.can_connect`**:

- `CRITICAL` if the the request to uri times out
- `UP` otherwise

**`ssl_cert.expiration`**:

The check returns:

- `CRITICAL` if the `uri`'s certificate has expired or will expire in less than `days_critical` days
- `WARNING` if the `uri`'s certificate expires in less than `days_warning` days
- `UP` otherwise

**`ssl_cert.is_valid`**:

Checks if certificate SNI, CN, and digital signature are valid.

- `CRITICAL` if any of the uri's certificate attributes listed above are invalid
- `UP` otherwise

### Events

TLS does not include any events.

## Troubleshooting

Need help? Contact [Datadog support][6].

[1]: https://en.wikipedia.org/wiki/Transport_Layer_Security
[2]: https://github.com/DataDog/integrations-core/blob/master/tls/datadog_checks/tls/data/conf.yaml.example
[3]: https://docs.datadoghq.com/agent/guide/agent-commands/?tab=agentv6#start-stop-and-restart-the-agent
[4]: https://docs.datadoghq.com/agent/guide/agent-commands/?tab=agentv6#agent-status-and-information
[5]: https://github.com/DataDog/integrations-core/blob/master/tls/metadata.csv
[6]: https://docs.datadoghq.com/help
