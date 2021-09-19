# Epidemic-dynamics-on-metapopulation-networks-with-node2vec-mobility

The data sets, numerical simulations, and Python codes are all presented in this directory.

All the data sets are included in the folder `data set`. The ER random graph, BA model, Random clustered graph, Power-law cluster graph, Geographical threshold graph, LFR model, US airport network, Manizales network presented in the paper are named as `ER-100-6-1.txt`, `BA-100-3-1.txt`, `random clustered graph indpendent 1.txt`, `powerlaw cluster graph p=0.5.txt`, `geographical threshold graph with threshold 80.txt`, `LFR model small mu.txt`, `USAir97-unweighted.txt`, and `colombian.txt`, respectively.

The code of Euler method in Fig. 2 and its Monte Carlo simulation is presented in `Fig. 2 Euler method and Monte Carlo simulation.ipynb`. For Euler method (cell [8]), the stepsize `h = 0.01` and its iteration times `iteration = 30000`. For Monte Carlo method (cell [11]), the stepsize `dt = 0.01` and it iterated 30000 times. (See the figure below). 


![Euler method](https://github.com/lingqime/Epidemic-dynamics-on-metapopulation-networks-with-node2vec-mobility/blob/main/images/image_1.png)

The heat map matrices presented in Figs. 4 and 5 are contained in the folder `Numerical results`. One can discern them by their nomenclatures. For example, `Epidemic threshold via ER-100-6-1 a, b.npy` represents the epidemic threshold on ER random graph in terms of a and b, i.e., Fig. 4(a) in the paper. 

All the numerical results were fulfilled by [Jupyter Notebook](https://jupyter.org/). The codes can be found in the folder `Codes`.

If there is any question, please email lingqime@buffalo.edu or lingqime@gmail.com.
