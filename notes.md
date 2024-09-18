## Notes

### 9/5/2024: Intro notes and information

### Cloud Serivce Providers
> - Azurerm / AWS / Google
1) **X as a Service (Xaas)**
    *  Infra (I) / Platform (P) / software (S) / database (D) / AI (AI) / function (F)

2) Labs
> - Exploring Edge Platofrms
> - Pruning 
> - Quantization
> - Neural Arch search
> - LLM compression


### 9/12 - 9/17
> - data center edge -> network Nodes -> Edge Devices / On-prem edge nodes

#### Edge infra
* Data Processing
> - Collection, Filtering, Cleansing, Transformation, Aggregation
* Cache and Storage
> - Temp Storage (Cache),  Perm Storage, Design Consideration
* Communication
> - Lower Latency, Improved Performanace (Local Data Proc, Impr Bandwidth Eff., Scalable)
* Content Delivery
> - CDN (Content Delivery Network), replicated among edge nodes, content route, Load balance, Dyn. cont optim.

### Edge Computation Models
#
#### Mobile/Multi-access Edge Computing
#### Cloudlet computing

### Colab Models
* Edge - Edge 
* Edge - Cloud
* Edge Device
* Cloud - Edge Device

### Picking the Right Model
#### Caching
* Caching for certin at home commands. If the command isn't cached (miss), move to cloud for computation
> - Check cache, if miss then rely on connection
#### Caching Framework
Request from user -> ```Command Interface``` 

## Exact to Semantic Deuplication
### Precise/Fuzzy redundancy: ```syntactic same/similar``` 
Looking at two different angles of oakland campus. Based on intent, this could be the same or different. Different photo, but the same location. 

Different ways to ask for a task, could we implement this to a standard task? Leaning model.

Semantic Red. Lookup

Feature extraction -> Similarity Match -> Cache Lookup

**This seems bias, because this threshold could be consistently missed based on phanetics of the user.**
Could this be adjusted? 

Could a Cloud + Edge model also have an "Edge" only version under certain circumstances? Is this possible? Do we include local processing in this case or limit functionality? Best practices?


**Federative Learning** for Hospitals and usage with DRL models. 

Enable cheaper Hardware to process information and models.

FPGA are fast but more costly compared to MC/Arduino, but are almost required to provide processing power lacked by the ladder. 

## Project Idea
Project would be Edge devices (preferably using an Pynq if possible) to compute data more efficiently with usign software and CPU to handle fp and general user interfacing. 