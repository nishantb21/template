# Save

This folder serves the sole purpose of saving weights and logs of training. Ideally metadata should be saved on a run by run basis. Each run should contain the logs, the saved weights(both checkpoint and final) and the config (see core package). The structure would probably be of the form 

```
save
    --run_1
        --logs
        --weights
        --config.json
    --run_2
        --logs
        --weights
        --config.json
    --run_2
        --logs
        --weights
        --config.json
```

This structure makes it easy to log metadata not just about the training but also the hyperparameters which can be crucial in a research environment.