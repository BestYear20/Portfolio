# Introduction

## About Me

I am 

## Informations

>**Payment**
- Pay Range
  - **Per Hour:** $50/h **-** $70/h
  - **Per Task:** $350+ **/** R$100,000+
- Payment Methods
  - **Crypto -** *(10% OFF)* **BTC, ETH, XMR, USDC, USDT**
  - **PayPal -** *(F&F)*
  - **Robux -** *(devex rates)* **Group Payout**

>**Contact**
- Discord
  - **LD#6019**
- Twitter
  - **@LDev_ROBLOX**

# Modular Scripting

?> I work with mainstream frameworks and modules which helps other programmers edit and add new features to my existing work. On top of that my code is clear and easy to understand even for beginners.

```lua
function ServerService:GetUnlockedTextures(player)
	return DataManager:getData(player).GameData.textures
end

function ServerService.Client:PurchaseTexture(player, texture)
	return self.Server:PurchaseTexture(player, texture)
end

function ServerService.Client:GetEquippedTexture(player)
	return self.Server.TexturesPerPlayer[player]
end

function ServerService.Client:GetUnlockedTextures(player)
	return self.Server:GetUnlockedTextures(player)
end
```

## 2nd

> Hey this is test