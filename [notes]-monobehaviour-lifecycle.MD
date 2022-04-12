
### Awake(): objects/instances are created and initialized

- Is called first
- Is called only once in a script lifecycle
- Is executed even if script is not enabled
- Is best for initializing the current object's properties or variables; which do not depend upon other object's property or variable value
- If you want to initialize the current object's properties or variables, which depend upon other object's properties or variables, then you must initialize them using Start method 

---

### OnEnable(): immediately script is enabled

- After Awake methos is executed immediately OnEnable event method is called
- Is also called whenever the script gets enabled
- Is best for resetting object properties or variables or executing some code; whenever a script gets enabled

---

### OnApplicationPause(): game application comes to foreground

- Is called after OnEnabled, if script is enabled or is called after Awake, if script is not enabled
- Is also called whenever game application goes to background and comes to foreground
- Whenever a game application comes to foreground it receives False value, which indicates game application is currently running
- Whenever a game application goes to background it receives True value, which indicates game applications is currently paused

---

### OnApplicationFocus(): immediately game application gets focus

- Is called immediately after OnApplicationPause
- Is also called whenever game application gets focus and gets defocus
- Whenever a game application comes to foreground it receives True value, which indicates game application has focus
- Whenever a game application goes to background it receives False value, which indicates game application fas defocus
- Is best to check whether game application is currently in focus or not

---

### Start(): first frame of the scene is created

- Is called after Awake, OnEnable, OnApplicationPause and OnApplicationFocus
- Is called only once in a script lifecycle
- Is executed only if script is enabled
- Is best for initializing the current object's properties or variables; which depend upon other object's property or variable value
- If you want to initialize the current object's properties or vairables, which depend upon other object's property or variable value, then you mus initialize them inside Start method

---

**OBS1: Update methods are executed only if script is enabled**

##### After first frame of the scene is created, it is going to be continuously updated and rendered by update methods:

### FixedUpdate()

- Is called after every predefined fixed time interval
- FixedUpdate is independent of game's frame refresh rate. Wheter game is runnint at 30FPS, 60FPS or 100FPS does not matter; it always called after every 0.02 sec (but it can be changed in _Edit - Project Settings - Time - Fixed Time Step - 0.02 sec_
- Is best for physics based updates (move game object by applying some force or rotate game object by applying some torque)

---

### Update(): continuously frame gets updated and rendered

- Is called once per frame continuously, depends upon game's frame refresh rate
- Frame refresh rate is measured in FPS (Frames per second)
- If game is running at 30 FPS, then Update method is called 30 times per second
- If game is running at 60 FPS, then Update method is called 60 times per second
- Is best for any non physics based updates, receiving user inputs etc

---

### LateUpdate()

- Is called once after every Update method call
- Is best for keeping track of current game object's or other game object's update
- For example, if you want to move the camera with respect to player movement, then first player should be moved then the camera. So player movement code must be written in Update method, and camera movement code must be written in LateUpdate method

---

### OnGUI()

- Is called many times per frame
- Is best for drawing GUI elements and handling UI events (like click event)
