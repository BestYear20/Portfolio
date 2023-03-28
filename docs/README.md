# Introduction

## About Me

I am a **Full-Stack** ROBLOX developer from Poland :poland:. I have **over 5 years** of programming experience. My timezone is `GMT+1`. I also code in `JS`, `TS` and `C#`.

## Informations

### Payment
- Pay Range
  - **Per Hour:** $50/h **-** $70/h
  - **Per Task:** $350+ **/** R$100,000+
- Payment Methods
  - **Crypto -** *(10% OFF)* **BTC, ETH, XMR, USDC, USDT**
  - **PayPal -** *(F&F)*
  - **Robux -** *(devex rates)* **Group Payout**

---

### Contact
- Discord
  - **LD#6019** `972018685826981918`
- Twitter
  - **@LDev_ROBLOX**

# Modular Scripting

?> I work with mainstream frameworks and modules which helps other programmers edit and add new features to my existing work. On top of that my code is clear and easy to understand even for beginners.

## Example Modules

### 1. Knit

---

#### Creating Service

```text
└── ServerScriptService
    └── Game
        └── Services
            ├── TexturesService.lua
            └── ... 
```
```lua
-- [[ Service ]] --
local ServerService = Knit.CreateService {
	Name = script.Name;
	TexturesPerPlayer = {};
	Client = {};
}
```


?> Here is piece of code allowing client to get `textures` player owns straight from server.

```lua
function ServerService:GetUnlockedTextures(player)
	return DataManager:getData(player).GameData.textures
end

function ServerService.Client:GetUnlockedTextures(player)
	return self.Server:GetUnlockedTextures(player)
end
```