from pybricks.hubs import EV3Brick
from pybricks.ev3devices import Motor
from pybricks.parameters import Port, Stop
from pybricks.tools import wait

# Inicializa o EV3 e os motores
ev3 = EV3Brick()
motor_tromba = Motor(Port.A)  # Motor que move a tromba
motor_pata_frontal = Motor(Port.B)  # Motor que move a pata frontal
motor_pata_traseira = Motor(Port.C)  # Motor que move a pata traseira

# Função para mover a tromba do elefante
def mover_tromba(graus):
    motor_tromba.run_target(100, graus, then=Stop.HOLD, wait=True)
    wait(500)

# Função para mover as patas do elefante
def mover_patas(graus_frontal, graus_traseira):
    motor_pata_frontal.run_target(100, graus_frontal, then=Stop.HOLD, wait=True)
    motor_pata_traseira.run_target(100, graus_traseira, then=Stop.HOLD, wait=True)
    wait(500)

# Função para emitir som de elefante
def som_de_elefante():
    ev3.speaker.beep(frequency=400, duration=500)  # Emite um som
    wait(500)
    ev3.speaker.play_file(SoundFile.ELEPHANT_CALL)  # Som de elefante pré-definido (caso exista no EV3)

# Função principal para controlar o elefante
def main():
    ev3.speaker.beep()  # Sinal de início
    wait(1000)

    # Exemplo de movimentação da tromba e patas
    mover_tromba(90)  # Levanta a tromba
    mover_patas(45, -45)  # Movimenta as patas (avançar)
    som_de_elefante()  # Emite um som de elefante
    wait(1000)

    mover_tromba(-90)  # Abaixa a tromba
    mover_patas(-45, 45)  # Movimenta as patas (recuar)
    wait(1000)

if __name__ == "__main__":
    main()

