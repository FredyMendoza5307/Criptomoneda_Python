# Criptomoneda_Python

Crea tu propia criptomoneda con Python (con código fuente)

El siguiente es el modelo básico del algoritmo blockchain para crear PyCoin:

class Block:
    def __init__():
#La primera categoría de bloque
        pass
 
    def calculate_hash():   
 #Calcular el valor hash de cada bloque
 
 
class BlockChain:
 
    def __init__(self):
      # Método de construcción 
    pass
 
    def construct_genesis(self):
 # Construye el bloque inicial
        pass
 
    def construct_block(self, proof_no, prev_hash):
 # Construye un nuevo bloque y agrégalo a la cadena de bloques
        pass
 
    @staticmethod
    def check_validity():
 Comprueba si la cadena de bloques es válida
        pass
 
    def new_data(self, sender, recipient, quantity):
 # Agregar datos de una nueva transacción
        pass
 
    @staticmethod
    def construct_proof_of_work(prev_proof):
 # Evite que blockchain sea atacado
        pass
 
    @property
    def last_block(self):
 # Regresar al último bloque de la cadena
        return self.chain[-1]
        
       
       1. Crea la primera clase de bloque

La cadena de bloques se compone de múltiples bloques interconectados. Si se manipula un bloque, las otras partes de la cadena dejarán de ser válidas. De acuerdo con los conceptos anteriores, creamos las siguientes funciones iniciales similares a bloques <a href="https://tipo-de-cambio.com/binance-coin-bnb/binance-smart-chain/">binance smart chain</a>:

import hashlib
import time
 
class Block:
 
    def __init__(self, index, proof_no, prev_hash, data, timestamp=None):
        self.index = index
        self.proof_no = proof_no
        self.prev_hash = prev_hash
        self.data = data
        self.timestamp = timestamp or time.time()
 
    @property
    def calculate_hash(self):
        block_of_string = "{}{}{}{}{}".format(self.index, self.proof_no,
                                              self.prev_hash, self.data,
                                              self.timestamp)
 
        return hashlib.sha256(block_of_string.encode()).hexdigest()
 
    def __repr__(self):
        return "{} - {} - {} - {} - {}".format(self.index, self.proof_no,
                                               self.prev_hash, self.data,
                                               self.timestamp)
                                               
                                               
Como puede ver en el código anterior, hemos definido__init__() Función, que comenzaráBlockEl tiempo de clase se ejecuta, como cualquier otra clase en Python.

Definimos los siguientes parámetros para la función inicial:

self: CotizaciónBlockUna instancia de la clase, para que pueda acceder a los métodos y propiedades asociados con la clase;

index: Registra la posición de un bloque en la cadena de bloques;

proof_no: La cantidad generada durante la creación de un nuevo bloque (es decir, minería);

prev_hash: Se refiere al valor hash del bloque anterior;

data: Registre todas las transacciones completadas, como la cantidad de compra;

timestamp: Marca la marca de tiempo de la transacción

El segundo método de la clasecalculate_hashEl valor hash del bloque actual se generará a partir del valor hash del bloque anterior y el módulo de algoritmo SHA-256 se importará para obtener el valor hash del bloque.

Cuando se ingresa el valor en el algoritmo hash cifrado, la función devolverá una cadena de 256 bits que representa el contenido del bloque.

Es por eso que el blockchain tiene la característica de seguridad, porque cada bloque tiene un valor hash, y el valor hash dependerá del valor hash del bloque anterior. Por lo tanto, si alguien intenta alterar cualquier bloque de la cadena, otros bloques tendrán valores hash no válidos, destruyendo así toda la red blockchain.

El bloque final se verá así:

{
    "index": 2,
    "proof": 21,
    "prev_hash": "6e27587e8a27d6fe376d4fd9b4edc96c8890346579e5cbf558252b24a8257823",
    "transactions": [
        {'sender': '0', 'recipient': 'Quincy Larson', 'quantity': 1}
    ],
    "timestamp": 1521646442.4096143
}

Segundo, crea una clase de blockchain

Como sugiere el nombre, la idea principal de la cadena de bloques es "vincular" varios bloques entre sí. Entonces construiremos unblockchainClase, esta clase será fundamental para gestionar el funcionamiento de toda la cadena.blockchainLa clase tiene varios métodos auxiliares para completar tareas en la cadena de bloques.

A continuación, explicamos el papel de cada método en la clase:

a, método constructor

Este método garantiza que se pueda crear una instancia de la cadena de bloques.


class BlockChain:
 
    def __init__(self):
        self.chain = []
        self.current_data = []
        self.nodes = set()
        self.construct_genesis()
        
        
El siguiente es el papel de sus atributos:

self.chain: esta variable contiene todos los bloques;

self.current_data: esta variable guarda todos los bloques de transacciones completadas;

self.construct_genesis (): este método es responsable de construir el bloque inicial

b. Construye el bloque de génesis

Necesario en la cadena de bloquesconstruct_genesisMétodo para construir el bloque inicial de la cadena. Convencionalmente, este bloque es especial porque simboliza el comienzo de la cadena de bloques. Entonces solo necesitamos pasar algunos valores predeterminados aConstruct_blockMétodo para construirlo. Por ejemplo, podemos darproof_noconprev_hashAsigne un valor de cero.

def construct_genesis(self):
    self.construct_block(proof_no=0, prev_hash=0)
 
 
def construct_block(self, proof_no, prev_hash):
    block = Block(
        index=len(self.chain),
        proof_no=proof_no,
        prev_hash=prev_hash,
        data=self.current_data)
    self.current_data = []
 
    self.chain.append(block)
    return block
