1. **create cluster iam role:**
2. **create dedicated vpc using cloudformation template:**
3. **create eks cluster:**
4. **install iam auth amd kubectls on working instance:**

kubeconfig update
---------------
```
aws eks --region ap-south-1 update-kubeconfig --name eks-demo-cluster
export KUBECONFIG=~/.kube/config

```

5. create role for worker node
   policy: ekscni,workernodepolicy,ec2contaierread

 6. create worker node
 7. deploy sample app

[refer video](https://www.youtube.com/watch?v=aZd0UolVwD4)

1. **Fill in the details for each step, providing clear instructions:**
2. **Use additional Markdown formatting for clarity and visual appeal:**
  - Use headings (#, ##, ###) to organize content.
  - Create lists (-, *) for steps or options.
  - Add code blocks (````) for commands or code snippets.
  - Link to relevant resources using [text](link) syntax.'')
