# Introduction

## About Me

I am a **Full-Stack** ROBLOX developer from Poland :poland:. I have **over 5 years** of programming experience. My timezone is `GMT+1`. I also code in `JS`, `TS` and `C#`.

## Informations

### Payment
- Pay Range
  - **Per Hour:** $50/h **-** $70/h
  - **Paid Per Task:** $100+ **/** R$30,000+
- Payment Methods
  - **Crypto -** *(10% OFF)* **BTC, ETH, XMR, USDC, USDT**
  - **PayPal -** *(F&F)*
  - **Robux -** *(devex rates)* **Group Payout**

!> **Minimum Order:** $350 **/** R$100,000

---

### Contact
- Discord
  - **LD#6019** `972018685826981918`
- Twitter
  - **@LDev_ROBLOX**

# Modular Scripting

Modular scripting allows faster and cleaner workflow by reusing same function from multiple different sources which makes applying any changes/fixes easier.

?> I work with mainstream frameworks and modules which helps other programmers edit and add new features to my existing work. On top of that my code is clear and easy to understand even for beginners.

## Knit

**Knit** is a ROBLOX game framework which makes communication between client and server alot faster to code by avoiding creating remote events manually. Most ROBLOX programmers use `Knit` which makes it perfect framework for big projects with multiple programmers.

### Creating Service
```lua
-- [[ Service ]] --
local ServerService = Knit.CreateService {
	Name = script.Name;
	TexturesPerPlayer = {};
	Client = {
        UpdateTexture = Knit.CreateSignal();
        Texture = Knit.CreateProperty(1);
    };
}
```

### Service Functions

```lua
function ServerService:GetUnlockedTextures(player)
	return DataManager:getData(player).GameData.textures
end

function ServerService.Client:GetUnlockedTextures(player)
	return self.Server:GetUnlockedTextures(player)
end
```
### Service Initialization
```lua
function ServerService:KnitStart()
	-- [[ Services ]] --
	DataManager = Knit.GetService("DataManager")
	-- [[ Setup ]] --
	local function onPlayerAdded(player)
		self.TexturesPerPlayer[player] = {TextureId = 1}
	end
	local function onPlayerRemoving(player)
		self.TexturesPerPlayer[player] = nil
	end
	-- [[ Init ]] --
	for _,player in ipairs(Players:GetPlayers()) do
		coroutine.wrap(onPlayerAdded)(player)
	end
	Players.PlayerAdded:Connect(onPlayerAdded)
	Players.PlayerRemoving:Connect(onPlayerRemoving)
end

return ServerService
```

## Profile Service

## BigNum

**BigNum** allows you to store numbers as a `128-bit` signed integer, which pretty much eliminates the issue with `64-bit` signed integer limiting highest number that can be stored by server.

`64-bit` signed int cannot be higher than `9,223,372,036,854,775,807` which isnt the case for `128-bit`.

### Operations on BigNum Values
```lua
function ServerService:GiveCurrency(player, amount, skipGamepass)
	local data = DataManager:getData(player)
	if not skipGamepass and table.find(ReciptsHandler.Gamepasses[player], "Double_Coins") then
		amount = tostring(BigNum.new(amount) * BigNum.new(2))
	end
	data.GameData.values.coins = tostring(BigNum.new(data.GameData.values.coins) + BigNum.new(amount))
	DataManager:Replicate(player)
	self.Client.Coins:SetFor(player, data.GameData.values.coins)
	self.Client.CoinFX:Fire(player, amount)
end
```

## FormatNumber

## Roact *(soon)*

# IDE And Version Management

?> **IDE:** `Visual Studio Code`.

?> **Version Management:** `Git` workflow which allows me to work with other programmers without interrupting them in unnecessary ways.

> I can use `Rojo` if I am the committing programmer or working solo.

# Math

## Functions