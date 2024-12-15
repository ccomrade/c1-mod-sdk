cmake_minimum_required(VERSION 3.15)

################################################################################

project(MyMod LANGUAGES CXX RC)

################################################################################

if(NOT MSVC)
	# Crysis requires MSVC ABI
	message(FATAL_ERROR "MSVC is the only supported compiler!")
endif()

if(NOT CMAKE_MSVC_RUNTIME_LIBRARY)
	# use statically linked MSVC runtime library
	# we don't want to bother our users with installing additional Visual C++ Redistributable
	set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()

################################################################################

add_library(${CMAKE_PROJECT_NAME} MODULE
	Code/Mod/AVMine.cpp
	Code/Mod/Actor.cpp
	Code/Mod/Alien.cpp
	Code/Mod/AmmoParams.cpp
	Code/Mod/AmmoPickup.cpp
	Code/Mod/Automatic.cpp
	Code/Mod/Beam.cpp
	Code/Mod/Binocular.cpp
	Code/Mod/Bullet.cpp
	Code/Mod/BulletTime.cpp
	Code/Mod/Burst.cpp
	Code/Mod/C4.cpp
	Code/Mod/C4Detonator.cpp
	Code/Mod/C4Projectile.cpp
	Code/Mod/Charge.cpp
	Code/Mod/Claymore.cpp
	Code/Mod/ClientSynchedStorage.cpp
	Code/Mod/CompatibilityAlienMovementController.cpp
	Code/Mod/DebugGun.cpp
	Code/Mod/Detonate.cpp
	Code/Mod/DllMain.cpp
	Code/Mod/EMPField.cpp
	Code/Mod/Environment/BattleDust.cpp
	Code/Mod/Environment/FlowTornado.cpp
	Code/Mod/Environment/Shake.cpp
	Code/Mod/Environment/Tornado.cpp
	Code/Mod/Fists.cpp
	Code/Mod/FlashAnimation.cpp
	Code/Mod/FlowItemAnimation.cpp
	Code/Mod/FlowVehicleNodes.cpp
	Code/Mod/FreezingBeam.cpp
	Code/Mod/Game.cpp
	Code/Mod/GameActions.cpp
	Code/Mod/GameCVars.cpp
	Code/Mod/GameDll.cpp
	Code/Mod/GameDll.rc
	Code/Mod/GameFactory.cpp
	Code/Mod/GameRules.cpp
	Code/Mod/GameRulesClientServer.cpp
	Code/Mod/GrabHandler.cpp
	Code/Mod/GunTurret.cpp
	Code/Mod/HUD/GameFlashAnimation.cpp
	Code/Mod/HUD/GameFlashLogic.cpp
	Code/Mod/HUD/HUD.cpp
	Code/Mod/HUD/HUDAirStrike.cpp
	Code/Mod/HUD/HUDCommon.cpp
	Code/Mod/HUD/HUDCrosshair.cpp
	Code/Mod/HUD/HUDInterfaceEffects.cpp
	Code/Mod/HUD/HUDMissionObjectiveSystem.cpp
	Code/Mod/HUD/HUDObituary.cpp
	Code/Mod/HUD/HUDObject.cpp
	Code/Mod/HUD/HUDPDA.cpp
	Code/Mod/HUD/HUDPowerStruggle.cpp
	Code/Mod/HUD/HUDRadar.cpp
	Code/Mod/HUD/HUDScopes.cpp
	Code/Mod/HUD/HUDScore.cpp
	Code/Mod/HUD/HUDSilhouettes.cpp
	Code/Mod/HUD/HUDSoundImpl.cpp
	Code/Mod/HUD/HUDTagNames.cpp
	Code/Mod/HUD/HUDTextArea.cpp
	Code/Mod/HUD/HUDTextChat.cpp
	Code/Mod/HUD/HUDTextEvents.cpp
	Code/Mod/HUD/HUDVehicleInterface.cpp
	Code/Mod/HUD/HUDWeaponAccessories.cpp
	Code/Mod/HUD/ScriptBind_HUD.cpp
	Code/Mod/HUD/Tweaks/HUDTweakMenu.cpp
	Code/Mod/HUD/Tweaks/TweakCommon.cpp
	Code/Mod/HUD/Tweaks/TweakMenu.cpp
	Code/Mod/HUD/Tweaks/TweakMetadata.cpp
	Code/Mod/HUD/Tweaks/TweakMetadataCVAR.cpp
	Code/Mod/HUD/Tweaks/TweakMetadataLUA.cpp
	Code/Mod/HUD/Tweaks/TweakTraverser.cpp
	Code/Mod/HomingMissile.cpp
	Code/Mod/Hunter.cpp
	Code/Mod/IronSight.cpp
	Code/Mod/Item.cpp
	Code/Mod/ItemAccessory.cpp
	Code/Mod/ItemClientServer.cpp
	Code/Mod/ItemDualWield.cpp
	Code/Mod/ItemEffect.cpp
	Code/Mod/ItemEvents.cpp
	Code/Mod/ItemParams.cpp
	Code/Mod/ItemResource.cpp
	Code/Mod/ItemScheduler.cpp
	Code/Mod/ItemSharedParams.cpp
	Code/Mod/ItemView.cpp
	Code/Mod/Lam.cpp
	Code/Mod/LaptopUtil.cpp
	Code/Mod/MPTutorial.cpp
	Code/Mod/Melee.cpp
	Code/Mod/Menus/CreateGame.cpp
	Code/Mod/Menus/FlashMenuObject.cpp
	Code/Mod/Menus/FlashMenuObjectOptions.cpp
	Code/Mod/Menus/FlashMenuObjectProfiles.cpp
	Code/Mod/Menus/FlashMenuObjectSingleplayer.cpp
	Code/Mod/Menus/FlashMenuScreen.cpp
	Code/Mod/Menus/GameNetworkProfile.cpp
	Code/Mod/Menus/MPHub.cpp
	Code/Mod/Menus/MPLobbyUI.cpp
	Code/Mod/Menus/MultiplayerMenu.cpp
	Code/Mod/Menus/OptionsManager.cpp
	Code/Mod/Menus/QuickGame.cpp
	Code/Mod/NanoSuit.cpp
	Code/Mod/NetInputChainDebug.cpp
	Code/Mod/NetPlayerInput.cpp
	Code/Mod/Nodes/FlowActorSensor.cpp
	Code/Mod/Nodes/FlowFadeNode.cpp
	Code/Mod/Nodes/FlowHitInfoNode.cpp
	Code/Mod/Nodes/FlowNanoSuitNodes.cpp
	Code/Mod/Nodes/FlowPlayerStagingNode.cpp
	Code/Mod/Nodes/FlowPostFXNodes.cpp
	Code/Mod/Nodes/HUDNodes.cpp
	Code/Mod/Nodes/MPNodes.cpp
	Code/Mod/Nodes/WeaponNodes.cpp
	Code/Mod/Observer.cpp
	Code/Mod/OffHand.cpp
	Code/Mod/Plant.cpp
	Code/Mod/Player.cpp
	Code/Mod/PlayerFeature.cpp
	Code/Mod/PlayerInput.cpp
	Code/Mod/PlayerMovement.cpp
	Code/Mod/PlayerMovementController.cpp
	Code/Mod/PlayerRotation.cpp
	Code/Mod/PlayerView.cpp
	Code/Mod/Projectile.cpp
	Code/Mod/Radio.cpp
	Code/Mod/Rapid.cpp
	Code/Mod/ReferenceWeapon.cpp
	Code/Mod/Rock.cpp
	Code/Mod/Rocket.cpp
	Code/Mod/RocketLauncher.cpp
	Code/Mod/SPAnalyst.cpp
	Code/Mod/Scan.cpp
	Code/Mod/Scope.cpp
	Code/Mod/Scout.cpp
	Code/Mod/ScreenEffects.cpp
	Code/Mod/ScriptBind_Actor.cpp
	Code/Mod/ScriptBind_Game.cpp
	Code/Mod/ScriptBind_GameRules.cpp
	Code/Mod/ScriptBind_Item.cpp
	Code/Mod/ScriptBind_Weapon.cpp
	Code/Mod/ScriptControlledPhysics.cpp
	Code/Mod/ScriptUtils.cpp
	Code/Mod/ServerSynchedStorage.cpp
	Code/Mod/Shark.cpp
	Code/Mod/SharkMovementController.cpp
	Code/Mod/ShotValidator.cpp
	Code/Mod/Shotgun.cpp
	Code/Mod/Single.cpp
	Code/Mod/SingleTG.cpp
	Code/Mod/SoundMoods.cpp
	Code/Mod/StdAfx.cpp
	Code/Mod/SynchedStorage.cpp
	Code/Mod/TacBullet.cpp
	Code/Mod/TagBullet.cpp
	Code/Mod/Throw.cpp
	Code/Mod/ThrowableWeapon.cpp
	Code/Mod/TracerManager.cpp
	Code/Mod/Trooper.cpp
	Code/Mod/VehicleActionAutomaticDoor.cpp
	Code/Mod/VehicleActionDeployRope.cpp
	Code/Mod/VehicleActionEntityAttachment.cpp
	Code/Mod/VehicleActionLandingGears.cpp
	Code/Mod/VehicleClient.cpp
	Code/Mod/VehicleDamageBehaviorBurn.cpp
	Code/Mod/VehicleDamageBehaviorCameraShake.cpp
	Code/Mod/VehicleDamageBehaviorCollisionEx.cpp
	Code/Mod/VehicleDamageBehaviorExplosion.cpp
	Code/Mod/VehicleDamageBehaviorTire.cpp
	Code/Mod/VehicleMovementAmphibious.cpp
	Code/Mod/VehicleMovementBase.cpp
	Code/Mod/VehicleMovementHelicopter.cpp
	Code/Mod/VehicleMovementHovercraft.cpp
	Code/Mod/VehicleMovementStdBoat.cpp
	Code/Mod/VehicleMovementStdWheeled.cpp
	Code/Mod/VehicleMovementTank.cpp
	Code/Mod/VehicleMovementTweaks.cpp
	Code/Mod/VehicleMovementVTOL.cpp
	Code/Mod/VehicleMovementWarrior.cpp
	Code/Mod/VehicleWeapon.cpp
	Code/Mod/Voting.cpp
	Code/Mod/Weapon.cpp
	Code/Mod/WeaponAttachmentManager.cpp
	Code/Mod/WeaponClientServer.cpp
	Code/Mod/WeaponEvent.cpp
	Code/Mod/WeaponInput.cpp
	Code/Mod/WeaponSystem.cpp
	Code/Mod/WorkOnTarget.cpp
)

################################################################################

# C++ version
set_property(TARGET ${CMAKE_PROJECT_NAME} PROPERTY CXX_STANDARD 17)

target_include_directories(${CMAKE_PROJECT_NAME}
	PRIVATE
		Code/CryEngine/CryAction
		Code/CryEngine/CryCommon
		Code/Mod
)
