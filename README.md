# Qiskit
Quantum CLI


### **Qiskit CLI Overview**

Qiskit CLI commands allow you to manage your Qiskit environment, execute quantum circuits, and interact with IBM Quantum backends.

### **1. Qiskit Installation**

Ensure you have Qiskit installed:
```bash
pip install qiskit
```

### **2. Qiskit CLI Commands**

#### **General Qiskit CLI Commands**
These commands help you get started and provide help information.

- **Display Qiskit version:**
  ```bash
  qiskit --version
  ```
  Output example:
  ```
  Qiskit 0.32.0
  ```

- **Get help for Qiskit CLI:**
  ```bash
  qiskit --help
  ```
  Output example:
  ```
  Usage: qiskit [OPTIONS] COMMAND [ARGS]...

  Options:
    --version  Show the version and exit.
    --help     Show this message and exit.

  Commands:
    execute  Execute a quantum circuit.
    backends  Manage and list available backends.
    status    Check the status of IBM Quantum systems.
  ```

#### **3. Execute Quantum Circuits**

- **Execute a Qiskit circuit:**
  ```bash
  qiskit execute my_circuit.qasm
  ```
  This command takes a QASM file and executes it on the specified backend.

  Example QASM file (`my_circuit.qasm`):
  ```qasm
  OPENQASM 2.0;
  include "qelib1.inc";
  qreg q[2];
  creg c[2];
  h q[0];
  cx q[0], q[1];
  measure q[0] -> c[0];
  measure q[1] -> c[1];
  ```

- **Execute a Qiskit circuit with specified backend and shots:**
  ```bash
  qiskit execute my_circuit.qasm --backend ibmq_athens --shots 1024
  ```

- **Execute a Qiskit circuit with IBM Quantum Experience token:**
  ```bash
  qiskit execute my_circuit.qasm --token YOUR_IBM_Q_EXPERIENCE_TOKEN
  ```

#### **4. Manage and List Backends**

- **List all available backends:**
  ```bash
  qiskit backends
  ```
  Output example:
  ```
  ibmq_qasm_simulator
  ibmqx2
  ibmq_16_melbourne
  ibmq_athens
  ```

- **Get details of a specific backend:**
  ```bash
  qiskit backends --backend ibmq_athens
  ```
  Output example:
  ```
  Backend: ibmq_athens
  Status: active
  Qubits: 5
  ```

- **Check the status of all IBM Quantum backends:**
  ```bash
  qiskit status
  ```
  Output example:
  ```
  Backend: ibmq_qasm_simulator  Status: active
  Backend: ibmqx2               Status: active
  Backend: ibmq_16_melbourne    Status: active
  Backend: ibmq_athens          Status: active
  ```

#### **5. Managing IBM Quantum Account**

- **Save IBM Quantum Experience token:**
  ```bash
  qiskit account save --token YOUR_IBM_Q_EXPERIENCE_TOKEN
  ```

- **Load IBM Quantum Experience token:**
  ```bash
  qiskit account load
  ```

- **Delete IBM Quantum Experience token:**
  ```bash
  qiskit account delete
  ```

- **List IBM Quantum Experience accounts:**
  ```bash
  qiskit account list
  ```

#### **6. Advanced Execution Options**

- **Run a circuit with optimization level:**
  ```bash
  qiskit execute my_circuit.qasm --backend ibmq_athens --optimization_level 3
  ```

- **Run a circuit with custom transpiler settings:**
  ```bash
  qiskit execute my_circuit.qasm --backend ibmq_athens --transpile --basis_gates u1,u2,u3,cx --coupling_map linear
  ```

- **Run a circuit with noise model:**
  ```bash
  qiskit execute my_circuit.qasm --backend ibmq_qasm_simulator --noise_model noise_model.json
  ```

  Example noise model file (`noise_model.json`):
  ```json
  {
      "errors": [
          {
              "type": "qerror",
              "operations": ["u1", "u2", "u3"],
              "gate_qubits": [[0]],
              "probabilities": [0.001, 0.001, 0.001],
              "gate_errors": [
                  {
                      "name": "pauli_error",
                      "params": [0.001]
                  }
              ]
          },
          {
              "type": "qerror",
              "operations": ["cx"],
              "gate_qubits": [[0, 1]],
              "probabilities": [0.02],
              "gate_errors": [
                  {
                      "name": "pauli_error",
                      "params": [0.02]
                  }
              ]
          }
      ]
  }
  ```

### **7. Miscellaneous Commands**

- **View Qiskit configuration:**
  ```bash
  qiskit config view
  ```

- **Set Qiskit configuration:**
  ```bash
  qiskit config set --key "some_key" --value "some_value"
  ```

- **Clear Qiskit configuration:**
  ```bash
  qiskit config clear
  ```

- **Qiskit Terra information:**
  ```bash
  qiskit info terra
  ```

- **Qiskit Aer information:**
  ```bash
  qiskit info aer
  ```

### **8. Using Qiskit from within Scripts**

You can also use Qiskit CLI commands from within scripts to automate quantum experiments and analyses. Here’s a simple example of a Python script that uses Qiskit CLI:

```python
import os

# Save IBM Quantum Experience token
os.system("qiskit account save --token YOUR_IBM_Q_EXPERIENCE_TOKEN")

# List available backends
os.system("qiskit backends")

# Execute a quantum circuit
os.system("qiskit execute my_circuit.qasm --backend ibmq_athens --shots 1024")

# Check the status of all IBM Quantum backends
os.system("qiskit status")
```

### **Conclusion**

This in-depth list covers a comprehensive range of Qiskit CLI commands, from basic operations to advanced execution options and configuration management. These commands enable efficient interaction with Qiskit and IBM Quantum systems, facilitating various quantum computing tasks directly from the command line.
