Task: Given the following file, write a CLI command to complete the objective:

Objective: submit a HTTP GET request to `https://example.com/api/:order_id` with Order IDs that are selling `TSLA`, writing to output to `./output.txt`
File: ./transaction-log.txt
### Considerations

1. This should be done in a single CLI command.
2. The machine is a x86 running Ubuntu 24.04.

Solution:
Here is the  command.But I usually write a bash shell script instead of a single cli command like this
jq -r 'select(.symbol=="TSLA" and .side=="sell") | "https://example.com/api/" + .order_id' transaction-log.txt | xargs -I {} curl -s {} >> output.txt