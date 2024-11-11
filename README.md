# Quantum Computing - Log Normal Distribution
The Log Normal Distribution is often used to model the price dynamics of assets, particularly in financial applications such as option pricing. To model the log-normal distribution on a quantum computer, we need to “load” the distribution onto a quantum state. This means encoding the probabilities of different outcomes of the asset price into quantum amplitudes.

There is already an implementation of quantum state preparation of the log-normal distribution using **1 qubit**, **2 qubits**, and **3 qubits** [1]. 

The goal of this project is to extend the existing implementation to prepare a quantum state using **4 qubits**. And also, write a generalized algorithm that can be used to prepare a quantum state using any number of qubits.

## Qubits Representation
### Single Qubit Representation
To produce the mentioned distribution using a single qubit in a quantum circuit, we use RY gates, where RY gates correspond to the following matrix:

![Screenshot from 2024-11-10 20-26-59](https://github.com/user-attachments/assets/bffc6241-9c22-4d06-9e68-c472ef488f31)

where 𝜃 is set to:

![Screenshot from 2024-11-10 20-27-32](https://github.com/user-attachments/assets/9f644fc2-b149-424d-811a-4eafdd68d78f)

The resulting state will be:

![Screenshot from 2024-11-10 20-28-38](https://github.com/user-attachments/assets/12f63af6-6e92-47f8-9ecc-6fb575fac962)

The corresponding quantum circuit is:

![Screenshot from 2024-11-11 12-31-48](https://github.com/user-attachments/assets/bcc03021-3f05-4768-8179-bfb9dde69828)

After calculating the qunatum state, we obtain:

![Screenshot from 2024-11-10 20-28-38](https://github.com/user-attachments/assets/28a4897d-2a52-4c7c-a335-18be7a93c701)

The probability distribution will be:

![Screenshot from 2024-11-11 12-46-37](https://github.com/user-attachments/assets/0b127b62-dd5a-4377-9d39-f84a7c3adc07)


### Two Qubits Repersentation
To prepare the distribution using two qubits, we must split the coefficient `P0` of `|0>` and assign the split values too `|00>` and `|01>` with the ratio `P00:P01`. Then we split the coefficient `P1` of `|1>` and assign those values to `|10>` and `|11>` with the ratio `P10:P11`. We can achieve this state using two additional RY gates with the two angles:

|![Screenshot from 2024-11-10 20-52-14](https://github.com/user-attachments/assets/e502b977-7668-4814-aca4-d974614d5a80) | ![Screenshot from 2024-11-10 20-52-22](https://github.com/user-attachments/assets/e4f10ff2-f7a3-4132-ae39-608d05ac094b) |

The corresponding quantum circuit is:

![Screenshot from 2024-11-11 12-37-26](https://github.com/user-attachments/assets/ff071359-bd66-44b5-888a-cede3c989a2e)

After calculating the qunatum state, we obtain:
![Screenshot from 2024-11-10 21-03-29](https://github.com/user-attachments/assets/5ace7527-c08b-4106-b484-b1d9cca70c4c)

The probability distribution will be:

![Screenshot from 2024-11-11 12-40-49](https://github.com/user-attachments/assets/28e66c04-9820-47c9-a5e8-d60b4afcfd65)


### Three Qubits Representation
We can use the same logic to prepare a quantum state with three qubits. The new required rotation angles will be: 

|![Screenshot from 2024-11-10 21-55-16](https://github.com/user-attachments/assets/9df0d5cd-afe1-4d8c-83e3-1d9b1efacedc)
 | ![Screenshot from 2024-11-10 21-55-23](https://github.com/user-attachments/assets/7f95e4a1-f7a2-42d5-9e19-e48765b82ffa)
 | ![Screenshot from 2024-11-10 21-55-31](https://github.com/user-attachments/assets/4cd072b9-76a1-4fee-aeb6-6613d1a56b3a)
 |  ![Screenshot from 2024-11-10 21-55-38](https://github.com/user-attachments/assets/61dd0c2b-31af-4f39-9170-2bd995919b75)
|

The resulting circuit will be:

![Screenshot from 2024-11-11 13-05-11](https://github.com/user-attachments/assets/7d1c6433-388b-4254-917d-0304978f05a1)

The probability distribution will be:

![Screenshot from 2024-11-11 13-07-00](https://github.com/user-attachments/assets/b8a75eaa-9edf-4008-ba10-08c651555a60)


### Four Qubit Representation
For the four-qubit representation, we were able to identify a pattern of the order of the application of RY gates, and created an algorithm that produces the quantum circuit for any given number of qubits. 
The new angles for the RY gates will be:
|![theta7](https://github.com/user-attachments/assets/86d468bb-f767-49c5-b3e1-04931cfd2e40)
 |![theta8](https://github.com/user-attachments/assets/9f5a0c3b-f7d2-4182-a826-fc65b46c0b53)
 |![theta9](https://github.com/user-attachments/assets/c7754c11-3e07-4302-9bf5-98fd21e32f20)
  | ![theta10](https://github.com/user-attachments/assets/f39f6abc-42b4-4fcb-9ac6-9fd62cf504e6)
 |
| ![theta11](https://github.com/user-attachments/assets/2976ce1d-1270-45f5-b684-80913f38baa1)
 |  | | |
## References
[1] https://medium.com/qiskit/systematic-preparation-of-arbitrary-probability-distribution-with-a-quantum-computer-165dfd8fbd7d
