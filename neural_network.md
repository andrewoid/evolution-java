# Basic Neural Network Library

https://github.com/kim-marcel/basic_neural_network

Download the library

``` shell

mkdir -p libs
curl -o libs/basic_neural_network-v0.5.1-jar-with-dependencies.jar https://raw.githubusercontent.com/andrewoid/evolution-java/refs/heads/main/neural_network/basic_neural_network-v0.5.2-jar-with-dependencies.jar

```

Add it as a dependency in build.gradle

``` groovy

implementation files('libs/basic_neural_network-v0.5.2-jar-with-dependencies.jar')

```

# Generic Algorithm

[Genetic Algorithms](https://en.wikipedia.org/wiki/Genetic_algorithm)

1. Construct 1000 random Neural Networks
1. For each network you are going to let it "play" the game and record the results.
1. To "Play", each time through your game loop you are going to ask the Neural Network what to do.

``` java
    
    double[] input = new double[1];
    input[0] = // angle from the ball to the paddle
    double[] answer = network.guess(input);
    
    if (answer[0] > answer[1]) {
        // paddle should go one direction
    }
    else  {
        // paddle should go another direction
    } 
    
```

1. Whatever networks perform the best, you are going to use them to construct more networks for the next generation.

``` java 

    // take the top 10 performing networks and use them
    // to construct 1000 more networks

    NeuralNetwork merged = network1.merge(network2);
    network.mutate(0.1);

```