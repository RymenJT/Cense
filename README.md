# Cense
// Los siguientes codigos son los Scripts que contiene el videojuego

//Player
extends KinematicBody2D

var motion = Vector2()
const velocidad = 100

func _physics_process(_delta):
	
	motion = Vector2(0,0)
	
	if Input.is_action_pressed("ui_right"):
		motion.x=velocidad
		$AnimationPlayer.play("Mover derecha")
	elif Input.is_action_pressed("ui_left"):
		motion.x=-velocidad
		$AnimationPlayer.play("Mover Izquierda")
	elif Input.is_action_pressed("ui_up"):
		motion.y=-velocidad
		$AnimationPlayer.play("Mover arriba")
	elif Input.is_action_pressed("ui_down"):
		motion.y=velocidad
		$AnimationPlayer.play("Mover abajo")
		
	else: 
			
			$AnimationPlayer.play("Stop")
			
	motion = move_and_slide(motion)

//Portals_Basics_structure
extends Area2D

export (String) var escena

func _on_Portal_body_entered(body):
	if body.name == "Player":
		get_tree().change_scene("res://Scenes/"+escena+".tscn")// Aqui se pone la ruta de la ubicacion de el mapa a cambiar
	pass # Replace with function body.
