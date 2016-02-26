package driverModule

const N_BUTTONS = 3
const N_FLOORS = 4
const (
	UP    = 0x01
	DOWN  = 0x02
	STILL = 0x03
)

var lampChannelMatrix = [N_FLOORS][N_BUTTONS]int{
	{LIGHT_UP1, LIGHT_DOWN1, LIGHT_COMMAND1},
	{LIGHT_UP2, LIGHT_DOWN2, LIGHT_COMMAND2},
	{LIGHT_UP3, LIGHT_DOWN3, LIGHT_COMMAND3},
	{LIGHT_UP4, LIGHT_DOWN4, LIGHT_COMMAND4}}

var buttonChannelMatrix = [N_FLOORS][N_BUTTONS]int{
	{BUTTON_UP1, BUTTON_DOWN1, BUTTON_COMMAND1},
	{BUTTON_UP2, BUTTON_DOWN2, BUTTON_COMMAND2},
	{BUTTON_UP3, BUTTON_DOWN3, BUTTON_COMMAND3},
	{BUTTON_UP4, BUTTON_DOWN4, BUTTON_COMMAND4}}

type ElevButtonTypeT int

const (
	BUTTON_CALL_UP   = 0
	BUTTON_CALL_DOWN = 1
	BUTTON_COMMAND   = 2
)

func GetFloorSensorSignal() int {

	if ReadBit(SENSOR_FLOOR1) {
		return 0
	} else if ReadBit(SENSOR_FLOOR2) {
		return 1
	} else if ReadBit(SENSOR_FLOOR3) {
		return 2
	} else if ReadBit(SENSOR_FLOOR4) {
		return 3
	} else {
		return -1
	}
}

func GetButtonSignal(button ElevButtonTypeT, floor int) bool {

	if ReadBit(buttonChannelMatrix[floor][button]) {
		return true
	} else {
		return false
	}
}
func ElevSetSpeed(speed int){

	if (speed > 0){
	    ClearBit(MOTORDIR);
	}else if (speed < 0){
		SetBit(MOTORDIR);
		speed = -speed;
	}

	WriteAnalog(MOTOR, speed);
}

func ElevStartEngine(direction int){

	if (direction == UP){
		ClearBit(MOTORDIR)
	}else {
		SetBit(MOTORDIR)
	}

	WriteAnalog(MOTOR, 2800);
}

func ElevStop(){
	WriteAnalog(MOTOR, 0);
  }
