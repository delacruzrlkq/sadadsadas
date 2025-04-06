-- Anime Vanguards de Dupe

local cartas = {
 {nome = "Naruto", ataque =10, defesa =5, traits = {"Velocidade"}},
 {nome = "Goku", ataque =15, defesa =10, traits = {"Força"}},
 {nome = "Lelouch", ataque =12, defesa =8, traits = {"Inteligência"}}
}

local deck = {}
for i =1,5 do table.insert(deck, cartas[math.random(1, #cartas)]) end

local tela = script.Parent
tela:ClearAllChildren()

for i, carta in pairs(deck) do
 local textLabel = Instance.new("TextLabel")
 textLabel.Parent = tela
 textLabel.Text = carta.nome
 textLabel.Position = UDim2.new(0, (i -1) *100,0,100)
end

local function alterarTraits()
 local cartaSelecionada = deck[math.random(1, #deck)]
 table.insert(cartaSelecionada.traits, "Nova Característica")
 tela:ClearAllChildren()
 for i, carta in pairs(deck) do
 local textLabel = Instance.new("TextLabel")
 textLabel.Parent = tela
 textLabel.Text = carta.nome
 textLabel.Position = UDim2.new(0, (i -1) *100,0,100)
 end
end

script.Parent.MouseClick:Connect(alterarTraits)
