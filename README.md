-- Anime Vanguards de Dupe

-- Define as cartas
local cartas = {
 {nome = "Naruto", ataque = 10, defesa = 5, traits = {"Velocidade"}},
 {nome = "Goku", ataque = 15, defesa = 10, traits = {"Força"}},
 {nome = "Lelouch", ataque = 12, defesa = 8, traits = {"Inteligência"}}
}

-- Função para criar um novo deck
local function criarDeck()
 local deck = {}
 for i = 1, 5 do
 local carta = cartas[math.random(1, #cartas)]
 table.insert(deck, carta)
 end
 return deck
end

-- Função para mostrar o deck
local function mostrarDeck(deck)
 -- Aqui você pode usar a API do Roblox para criar uma interface gráfica
 -- Por exemplo:
 local tela = Instance.new("ScreenGui")
 tela.Parent = game.StarterGui
 local frame = Instance.new("Frame")
 frame.Parent = tela
 frame.Size = UDim2.new(1, 0, 1, 0)
 
 for i, carta in pairs(deck) do
 local textLabel = Instance.new("TextLabel")
 textLabel.Parent = frame
 textLabel.Text = carta.nome
 textLabel.Position = UDim2.new(0, (i - 1) * 100, 0, 100)
 end
end

-- Função para alterar traits
local function alterarTraits(carta, trait)
 table.insert(carta.traits, trait)
end

-- Função para rollback dos traits
local function rollbackTraits(carta, historico)
 carta.traits = historico[#historico]
end

-- Cria o deck inicial
local deck = criarDeck()
local historicoTraits = {}

-- Loop principal
while true do
 -- Aqui você pode usar a API do Roblox para lidar com eventos
 -- Por exemplo:
 wait(1)
 
 -- Alterar traits
 local cartaSelecionada = deck[math.random(1, #deck)]
 alterarTraits(cartaSelecionada, "Nova Característica")
 table.insert(historicoTraits, cartaSelecionada.traits)
 
 -- Mostrar deck
 mostrarDeck(deck)
 
 -- Verificar se o jogador pressionou a tecla R
 -- (isso pode ser feito usando a API do Roblox)
 
 -- Rollback dos traits
 -- rollbackTraits(cartaSelecionada, historicoTraits)
end
