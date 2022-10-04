# Unity Editor Observer
An editor tool that allows you to easily test your methods.

# Usage
Add your methods with `SimpleObserver` class as you see in the example code.  
Open Observer panel from `MD/Simple Observer` under editor tool menu. The methods will appear at runtime.  

|Editor Time|Run Time|
|----|---|
|<img src="/.github/screenshots/SOeditorTime.png">|<img src="/.github/screenshots/SORunTime.png">|


## Example
```c
public class TEST : MonoBehaviour
{
    private GameManager m_GameManager;
    private void Awake()
    {
        SimpleObserver.AddCallback(LevelComplete);
        SimpleObserver.AddCallback(LevelFail);
        SimpleObserver.AddCallback(RestartLevel);
        SimpleObserver.AddCallback(NextLevel);
#if SCENE_MODE
        SimpleObserver.AddCallback(LoadMainMenu);
#endif
        m_GameManager = GameManager.Instance as GameManager;
    }
    
#if SCENE_MODE
    private void LoadMainMenu()
    {
        m_GameManager.LoadMainMenu();
    }
#endif

    private void NextLevel()
    {
        m_GameManager.NextLevel();
    }

    public void LevelComplete()
    {
        m_GameManager.CompleteLevel();
    }

    public void LevelFail()
    {
        m_GameManager.FailLevel();
    }

    private void RestartLevel()
    {
        m_GameManager.RestartLevel();
    }
}
```` 
