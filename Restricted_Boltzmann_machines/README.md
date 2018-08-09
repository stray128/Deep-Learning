*Boltzmann Machines*
-------------------
A Boltzmann machine (also called stochastic Hopfield network with hidden units) is a type of stochastic recurrent neural network (and Markov random field[citation needed]).

Boltzmann machines can be seen as the stochastic, generative counterpart of Hopfield nets. They were one of the first neural networks capable of learning internal representations, and are able to represent and (given sufficient time) solve difficult combinatoric problems.

They are theoretically intriguing because of the locality and Hebbian nature of their training algorithm, and because of their parallelism and the resemblance of their dynamics to simple physical processes. Boltzmann machines with unconstrained connectivity have not proven useful for practical problems in machine learning or inference, but if the connectivity is properly constrained, the learning can be made efficient enough to be useful for practical problems.

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7a/Boltzmannexamplev1.png/220px-Boltzmannexamplev1.png?raw=true "Boltzmann Machines")

Restricted Boltzmann Machines
-----------------------------
A restricted Boltzmann machine (RBM) is a generative stochastic artificial neural network that can learn a probability distribution over its set of inputs.

The difference between this and the conventional Boltzmann Macine Model is that the connections between the identical neurons are restricted.(i.e., there are connections only between hidden neurons and visible neurons)
![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e8/Restricted_Boltzmann_machine.svg/220px-Restricted_Boltzmann_machine.svg.png)

**Reference:**
  -https://pdfs.semanticscholar.org/dd13/5a89b5075af5cbef5becaf419457cdd77cc9.pdf

