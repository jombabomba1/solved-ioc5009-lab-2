Download Link: https://assignmentchef.com/product/solved-ioc5009-lab-2
<br>
<h1>1         Benchmarking Deep Neural Networks</h1>

People often estimate the number of parameters and MAC operations to take insight of one neural network model. Results of this benchmarking help people to optimize the computation of neural networks and neural network hardware designs.

This lab requires you to implement each neural network layer of VGG 16 model through high level programming languages such as C/C++/python(numpy and scipy) etc.. You don’t allow to using any external DNN libraries such as cuDNN, MKL-DNN or DNN frameworks such as pyTorch, TensorFlow and Keras in your implementation. You can follow VGG 16 model architecture model (See Table 1) to complete your <strong>forward pass </strong>implementation. You only require to run your implementation on the CPU. Furthermore, you also need to calculate the memory size of inputs, the number of parameters, and the number of MAC operations in each layer. The batch size of this VGG 16 model is 1. The activation function in CONV layer is ”ReLU”. The size of the initial input is 224 x 224 x 3 and the input’s values are randomly generated. Finally, you need to fill your results in the VGG16 Benchmark Table (See Table 2) and turn your codes and completed table in.

Table 1: VGG 16 Model Architecture

<table width="592">

 <tbody>

  <tr>

   <td width="86"> </td>

   <td width="72">Input</td>

   <td width="76">Filter Size</td>

   <td width="90"># of channel</td>

   <td width="74"># of filter</td>

   <td width="69">Pool Size</td>

   <td width="49">stride</td>

   <td width="76">Activation</td>

  </tr>

  <tr>

   <td width="86">INPUT</td>

   <td width="72">224 x 224</td>

   <td width="76"> </td>

   <td width="90">3</td>

   <td width="74">3</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">224 x 224</td>

   <td width="76">3 x 3</td>

   <td width="90">64</td>

   <td width="74">64</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">224 x 224</td>

   <td width="76">3 x 3</td>

   <td width="90">64</td>

   <td width="74">64</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69">2 x 2</td>

   <td width="49">2</td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">112 x 112</td>

   <td width="76">3 x 3</td>

   <td width="90">128</td>

   <td width="74">128</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">112 x 112</td>

   <td width="76">3 x 3</td>

   <td width="90">128</td>

   <td width="74">128</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69">2 x 2</td>

   <td width="49">2</td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">56 x 56</td>

   <td width="76">3 x 3</td>

   <td width="90">256</td>

   <td width="74">256</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">56 x 56</td>

   <td width="76">3 x 3</td>

   <td width="90">256</td>

   <td width="74">256</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">56 x 56</td>

   <td width="76">3 x 3</td>

   <td width="90">256</td>

   <td width="74"> </td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69">2 x 2</td>

   <td width="49">2</td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">28 x 28</td>

   <td width="76">3 x 3</td>

   <td width="90">512</td>

   <td width="74">512</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">28 x 28</td>

   <td width="76">3 x 3</td>

   <td width="90">512</td>

   <td width="74">512</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">28 x 28</td>

   <td width="76">3 x 3</td>

   <td width="90">512</td>

   <td width="74">512</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69">2 x 2</td>

   <td width="49">2</td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">14 x 14</td>

   <td width="76">3 x 3</td>

   <td width="90">512</td>

   <td width="74">512</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">14 x 14</td>

   <td width="76">3 x 3</td>

   <td width="90">512</td>

   <td width="74">512</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="72">14 x 14</td>

   <td width="76">3 x 3</td>

   <td width="90">512</td>

   <td width="74">512</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69">2 x 2</td>

   <td width="49">2</td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">FC 4096</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">FC 4096</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">FC 1000</td>

   <td width="72"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76"> </td>

  </tr>

 </tbody>

</table>

Table 2: VGG 16 Benchmarking Table

<table width="489">

 <tbody>

  <tr>

   <td width="86"> </td>

   <td width="155">Memory Size</td>

   <td width="106"># of parameter</td>

   <td width="143"># of MAC operations</td>

  </tr>

  <tr>

   <td width="86">INPUT</td>

   <td width="155">224 x 224 x 3 = 150K</td>

   <td width="106">0</td>

   <td width="143">0</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="155">112 x 112 x 64 = 800 K</td>

   <td width="106">0</td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="155"> </td>

   <td width="106">0</td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="155"> </td>

   <td width="106">0</td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="155"> </td>

   <td width="106">0</td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="155"> </td>

   <td width="106">0</td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">FC 4096</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">FC 4096</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

  <tr>

   <td width="86">FC 1000</td>

   <td width="155"> </td>

   <td width="106"> </td>

   <td width="143"> </td>

  </tr>

 </tbody>

</table>

Figure 1: The prototype of a systolic array accelerator

<h1>2         Systolic Array Architecture</h1>

The systolic array accelerator tailors for operations of DNN models. The accelerator contains a 2D array of processing elements (PE) to calculate matrix multiplication and convolution, an unified multi-bank buffer decomposed into input, weight and output buffers, and a SIMD vector unit for POOL, ACT, normalization, and etc..

This lab requires you to implement a systolic array accelerator by using verilog. Figure 1 presents the prototype of the systolic array accelerator. The specification of a systolic array accelerator is shown as follows:

<ol>

 <li>The size of PE array is 16 × 16.</li>

 <li>Each Processing element (PE) takes one cycle to calculate one MAC operation.</li>

 <li>The PE array can proceed the convolution and fully-connected operation through the systolicTable 3: TinyML Model Architecture</li>

</ol>

<table width="579">

 <tbody>

  <tr>

   <td width="86"> </td>

   <td width="58">Input</td>

   <td width="76">Filter Size</td>

   <td width="90"># of channel</td>

   <td width="74"># of filter</td>

   <td width="69">Pool Size</td>

   <td width="49">stride</td>

   <td width="76">Activation</td>

  </tr>

  <tr>

   <td width="86">INPUT</td>

   <td width="58">16 x 16</td>

   <td width="76"> </td>

   <td width="90">3</td>

   <td width="74">3</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="58">16 x 16</td>

   <td width="76">2 x 2</td>

   <td width="90">4</td>

   <td width="74">16</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="58"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69">2 x 2</td>

   <td width="49">2</td>

   <td width="76"> </td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="58">8 x 8</td>

   <td width="76">3 x 3</td>

   <td width="90">1</td>

   <td width="74">8</td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76">ReLU</td>

  </tr>

  <tr>

   <td width="86">FC 8</td>

   <td width="58"> </td>

   <td width="76"> </td>

   <td width="90"> </td>

   <td width="74"> </td>

   <td width="69"> </td>

   <td width="49"> </td>

   <td width="76"> </td>

  </tr>

 </tbody>

</table>

Table 4: TinyML Benchmarking Table

<table width="263">

 <tbody>

  <tr>

   <td width="86"> </td>

   <td width="50">cycles</td>

   <td width="128">Max PE utilization</td>

  </tr>

  <tr>

   <td width="86">INPUT</td>

   <td width="50">0</td>

   <td width="128">0</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="50"> </td>

   <td width="128"> </td>

  </tr>

  <tr>

   <td width="86">MAXPOOL</td>

   <td width="50"> </td>

   <td width="128">0</td>

  </tr>

  <tr>

   <td width="86">CONV</td>

   <td width="50"> </td>

   <td width="128"> </td>

  </tr>

  <tr>

   <td width="86">FC 8</td>

   <td width="50"> </td>

   <td width="128"> </td>

  </tr>

 </tbody>

</table>

execution manner.

<ol start="4">

 <li>No limit for buffer size and DRAM.</li>

 <li>There are 16 SIMD vector lanes. Each SIMD lane can complete POOL and ACT operation inone cycle.</li>

</ol>

You need to run a TinyML model shown in the table 3 on this systolic array accelerator and complete the table 4. Note that PE utilization indicates the max number of PE used by each layer.

Finally, you need to fill your results in the TinyML Benchmark Table (See Table 4) and turn your codes and completed table in.