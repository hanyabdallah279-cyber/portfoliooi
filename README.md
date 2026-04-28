graph TD
    Start(( )) --> OpenApp[User opens Smart Trainer app]
    OpenApp --> Login[User logs in or signs up]
    Login --> Auth{Is user authenticated?}
    
    Auth -- else --> Error[Show error]
    Error --> Login
    Auth -- authenticated --> StartSession[User starts exercise session]
    Auth -- Sign up --> SignUp[Sign up]
    SignUp --> StartSession

    StartSession --> Capture[User uploads/captures exercise image]
    Capture --> Detect[System detects pose landmarks]
    Detect --> Classify[System classifies posture]
    Classify --> Evaluate[System evaluates posture & calculates angles]
    Evaluate --> Feedback[System generates real-time feedback]
    
    Feedback --> HR{Is heart rate sensor connected?}
    HR -- yes --> BPM[Read BPM and display]
    BPM --> Results[System shows feedback and results]
    HR -- no --> Results
    
    Results --> EndSession[User ends the session]
    EndSession --> Stop(( ))
