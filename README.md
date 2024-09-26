# Juego de la Serpiente con IA utilizando Deep Q-Learning

Este proyecto implementa un agente de IA que juega al clásico juego de la Serpiente utilizando un algoritmo de deep Q-learning. La IA aprende a jugar el juego de manera autónoma mejorando su rendimiento a través de prueba y error, utilizando técnicas de aprendizaje por refuerzo.

## Descripción del Agente

El archivo `agent.py` contiene la lógica principal del agente de IA. El agente está construido usando una red Q profunda (DQN), donde almacena los estados del juego, realiza acciones y entrena su red neuronal en función de las recompensas. El agente interactúa con el entorno del juego de la Serpiente y ajusta su estrategia con el tiempo modificando su política.

### Componentes Clave:

- **Representación del Estado**: El agente extrae el estado actual del juego, que incluye la posición de la serpiente, la dirección de movimiento, la proximidad a obstáculos y la ubicación de la comida. Este estado se representa como un conjunto de 11 características.
  
- **Selección de Acciones**: El agente selecciona acciones (moverse hacia adelante, girar a la izquierda o girar a la derecha) basándose en una política epsilon-greedy, equilibrando exploración y explotación.

- **Memoria**: Se utiliza una memoria de repetición para almacenar las transiciones del juego (`estado`, `acción`, `recompensa`, `siguiente_estado`, `finalizado`). Esto permite que el agente aprenda de experiencias pasadas y realice entrenamientos por lotes.

- **Entrenamiento**: El agente utiliza dos tipos de entrenamiento:
  1. **Entrenamiento a corto plazo**: El agente actualiza su red neuronal después de cada paso.
  2. **Entrenamiento a largo plazo**: Después de cada juego, el agente toma una muestra de experiencias de la memoria y realiza descenso de gradiente para actualizar la red.
  
- **Red Neuronal**: Una red neuronal completamente conectada (`Linear_QNet`), que consiste en una capa de entrada con 11 características, una capa oculta con 256 neuronas, y una capa de salida con 3 neuronas, que representan las acciones posibles.

### Interacción con el Juego

El archivo `game.py` maneja el entorno del juego utilizando Pygame. Define el bucle del juego, el movimiento de la serpiente y la detección de colisiones. El juego se actualiza continuamente a medida que el agente toma decisiones para mover la serpiente, recoger comida y evitar colisiones.

### Red Neuronal y Entrenador

El archivo `model.py` define la arquitectura de la red neuronal (`Linear_QNet`) y la lógica de entrenamiento (`QTrainer`). El entrenador calcula los valores Q utilizando el error cuadrático medio (MSE) como función de pérdida y el optimizador Adam para actualizar los pesos.

### Funciones Auxiliares

El archivo `helper.py` proporciona utilidades para graficar el rendimiento del agente a lo largo del tiempo, mostrando las puntuaciones del juego y el promedio móvil.

## Ejecución del Proyecto

Para ejecutar la IA del Juego de la Serpiente, simplemente ejecuta el archivo `agent.py`. El juego comenzará y el agente de IA empezará a entrenarse y mejorar su rendimiento.

```bash
python agent.py

