# 100 - Network Diagrams

## 100 - Power Bank Diagram

```mermaid
graph LR
subgraph Nitecore_GEN2["Nitecore GEN2 Energy Brick"]
    direction LR
    USBC[("USB-C Port<br/>Input: 5-20V<br/>Output: 5-20V")]
    USBA[("USB-A Port<br/>Output: 5V")]
end
style Nitecore_GEN2 fill:#f0f0f0,stroke:#333,stroke-width:3px,color:#000,font-weight:bold
style USBC fill:#2196F3,stroke:#333,stroke-width:2px,color:#fff
style USBA fill:#4CAF50,stroke:#333,stroke-width:2px,color:#fff
```

The diagram shows the Energy Brick housing containing a USB-C port that supports both input and output (5-20V) and a USB-A port that provides 5V output only.

## 200 - DC DC Step-Up Converter Diagram

```mermaid
graph LR
subgraph StepUpConverter["DC-DC Step-Up Converter"]
    direction LR
    Input[("Input: 5V")]  
    Output[("Output: 12V")]
end
style StepUpConverter fill:#f0f0f0,stroke:#333,stroke-width:3px,color:#000,font-weight:bold
style Input fill:#2196F3,stroke:#333,stroke-width:2px,color:#fff
style Output fill:#4CAF50,stroke:#333,stroke-width:2px,color:#fff
```

The diagram shows the DC-DC Step-Up Converter with an input port accepting 5V power source and an output port providing stepped-up 12V power. The voltage conversion happens within the converter housing, making it useful for powering 12V devices from 5V USB power sources.

## 300 - Shelly UNI Plus Diagram

```mermaid
%%{init: {'theme':'dark', 'themeVariables': { 'fontSize': '16px'}, "flowchart" : { "width": 1400, "height": 400, "diagramPadding": 50 }} }%%
graph LR
subgraph ShellyUNI["__ Shelly UNI Plus ___"]
    direction TB
    subgraph Inputs["Inputs"]
        direction LR
        VDC[("6 +5V")]
        GND[("7 GND")]
    end
    subgraph Outputs["Outputs"]
        direction LR
        Out1[("Output 1")]
        Out2[("Output 2")]
    end
end
style ShellyUNI fill:#2d2d2d,stroke:#333,stroke-width:3px,color:#fff,font-weight:bold
style Inputs fill:#1a1a1a,stroke:none
style Outputs fill:#1a1a1a,stroke:none
style VDC fill:#2196F3,stroke:#555,stroke-width:2px,color:#fff
style GND fill:#4CAF50,stroke:#555,stroke-width:2px,color:#fff
style Out1 fill:#ff9800,stroke:#555,stroke-width:2px,color:#fff
style Out2 fill:#ff9800,stroke:#555,stroke-width:2px,color:#fff
```

The diagram shows:
- VDC (Grey wire) - +5VDC power input on port 6
- GND (Turquoise wire) - Ground connection on port 7 
- Shelly UNI Plus device housing

## 400 - Electromagnet Diagram

```mermaid
%%{init: {'theme':'dark', 'themeVariables': { 'fontSize': '16px'}, "flowchart" : { "width": 1400, "height": 400, "diagramPadding": 50 }} }%%
graph LR
subgraph Electromagnet["__ Electromagnet ___"]
    direction TB
    subgraph Inputs["Inputs"]
        direction LR
        Pin1[("12V")]
        Pin2[("GND")]
    end
end
style Electromagnet fill:#2d2d2d,stroke:#333,stroke-width:3px,color:#fff,font-weight:bold
style Inputs fill:#1a1a1a,stroke:none
style Pin1 fill:#2196F3,stroke:#555,stroke-width:2px,color:#fff
style Pin2 fill:#4CAF50,stroke:#555,stroke-width:2px,color:#fff
```

## 900 - Assembly Diagram

```mermaid
%%{init: {'theme':'dark', 'themeVariables': { 'fontSize': '16px'}, "flowchart" : { "width": 2000, "height": 1000, "diagramPadding": 100 }} }%%
graph LR
    subgraph Nitecore_GEN2["__ Nitecore GEN2 Energy Brick ___"]
        direction LR
        USBC[("USB-C Port<br/>Input: 5-20V<br/>Output: 5-20V")]
        USBA[("USB-A Port<br/>Output: 5V")]
    end

    subgraph StepUpConverter["__ DC-DC Step-Up Converter ___"]
        direction LR
        Input[("Input: 5V")]  
        Output[("Output: 12V")]
    end

    subgraph ShellyUNI["__ Shelly UNI Plus ___"]
        direction TB
        VDC5[("6 +5V")]
        GND[("7 GND")]
        Out1[("Output 1")]
        Out2[("Output 2")]
    end

    subgraph Electromagnet1["__ Electromagnet 1 ___"]
        direction LR
        Mag1_In[("12V")]
        Mag1_GND[("GND")]
    end

    subgraph Electromagnet2["__ Electromagnet 2 ___"]
        direction LR
        Mag2_In[("12V")]
        Mag2_GND[("GND")]
    end

    USBA ====>|"5V USB Cable"| Input
    Output ====>|"12V"| VDC5
    Out1 ====>|"12V"| Mag1_In
    Out2 ====>|"12V"| Mag2_In
    Nitecore_GEN2 ===|"Common Ground"| StepUpConverter
    StepUpConverter ===|"Common Ground"| ShellyUNI
    ShellyUNI ===|"Common Ground"| Electromagnet1
    ShellyUNI ===|"Common Ground"| Electromagnet2

    style Nitecore_GEN2 fill:#f0f0f0,stroke:#333,stroke-width:3px,color:#000,font-weight:bold
    style StepUpConverter fill:#f0f0f0,stroke:#333,stroke-width:3px,color:#000,font-weight:bold
    style ShellyUNI fill:#2d2d2d,stroke:#333,stroke-width:3px,color:#fff,font-weight:bold
    style Electromagnet1 fill:#2d2d2d,stroke:#333,stroke-width:3px,color:#fff,font-weight:bold
    style Electromagnet2 fill:#2d2d2d,stroke:#333,stroke-width:3px,color:#fff,font-weight:bold
    style USBC fill:#2196F3,stroke:#333,stroke-width:2px,color:#fff
    style USBA fill:#4CAF50,stroke:#333,stroke-width:2px,color:#fff
    style Input fill:#2196F3,stroke:#333,stroke-width:2px,color:#fff
    style Output fill:#4CAF50,stroke:#333,stroke-width:2px,color:#fff
    style VDC5 fill:#2196F3,stroke:#555,stroke-width:2px,color:#fff
    style GND fill:#4CAF50,stroke:#555,stroke-width:2px,color:#fff
    style Out1 fill:#ff9800,stroke:#555,stroke-width:2px,color:#fff
    style Out2 fill:#ff9800,stroke:#555,stroke-width:2px,color:#fff
    style Mag1_In fill:#2196F3,stroke:#555,stroke-width:2px,color:#fff
    style Mag1_GND fill:#4CAF50,stroke:#555,stroke-width:2px,color:#fff
    style Mag2_In fill:#2196F3,stroke:#555,stroke-width:2px,color:#fff
    style Mag2_GND fill:#4CAF50,stroke:#555,stroke-width:2px,color:#fff
```

The assembly diagram now shows the complete power flow:
1. The Nitecore GEN2 Energy Brick provides 5V output through its USB-A port
2. This 5V is connected to the DC-DC Step-Up Converter input via a USB cable
3. The Step-Up Converter boosts the voltage to 12V
4. The 12V output connects to the Shelly UNI Plus VDC5 input (Note: Although labeled as +5V, this input accepts 12V which is required to power the electromagnets)
5. The Shelly UNI Plus outputs (1 & 2) connect to the respective electromagnets
6. Ground connections are maintained throughout the system