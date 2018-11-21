# ovs-vsctl
```bash
ovs-vsctl show
```



# ovs-ofctl user-level flow
```bash
ovs-ofctl show nsx-managed
ovs-ofctl dump-flows nsx-managed | ovs-decode-note
```

## Port statistics
```bash
ovs-ofctl dump-ports nsx-managed
```

# ovs-dpctl  kernel-level flow
```bash
ovs-dpctl show
ovs-dpctl dump-flows
ovs-dpctl dump-flows | findstr icmp
```


# ovs-appctl
```bash
ovs-appctl ofproto/trace nsx-managed in_port=1,dl_dst=01:80:c2:00:00:05
```
