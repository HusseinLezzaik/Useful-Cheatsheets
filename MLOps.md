## Lessons from Industry:
- Data is actually more important than models
- Modeling libraries don't matter, as modelling is just a tiny step in the ml pipeline. For ex, it's much harder to migrate data pipeline code than rewrite basic TF modeling code in PyTorch.
- If you're a researcher or datascientist, don't build your pipeline around a specific library.
- There is a huge need for reproducibility
- ML monitoring is hard
- In practice, we work with streams of data, not fixed datasets or static datasets
- Data labelling is probably one of the most time consuming steps
- ML generalization gets fixed by scaling compute power
- Strategy of shifting as much compute as possible from inference time (where code is under strict latency requirements and doesn’t know the future) to training time
- Overfit to the most recent data and constantly retrain

## How to Manage ML Teams Better:
- Do ml project planning probabilistically (vs. waterfall approach) .. assign tasks with prob and parallelize tasks
- Important to build culture of the team
- Attempt a portfolio of approaches
- Measure progress based on inputs, not results (focus on execution and not on the results of the project)
- Have researchers and engineers work together
- Get end-to-end pipelines together quickly to demonstrate quick wins
- Educate leadership on ML timeline uncertainty
- Data Flywheel: more users -> more data -> better model
- Product design can reduce need for accuracy (grammarly to let users chose things for example)
