# Laravel Maps App - OpenStreetMap +

Leaflet Uma aplicação web completa desenvolvida em Laravel para gerenciamento de localizações geográficas com integração de mapas usando OpenStreetMap e Leaflet.

## 📋 Funcionalidades

- ✅ CRUD completo de localizações (nome, descrição, coordenadas, endereços, categoria)
- ✅ Mapas interativos em todas as visualizações usando Leaflet
- ✅ Seleção de seleções clicando no mapa
- ✅ Visualização de múltiplos marcadores no mapa principal
- ✅ API RESTful para integrações
- ✅ Interface responsiva com Bootstrap 5
- ✅ Validação de dados no frontend e backend

## 🛠️ Tecnologias Utilizadas

- **Backend:** Laravel 10+, PHP 8.2+
- **Frontend:** Bootstrap 5, Leaflet.js, Font Awesome
- **Banco de Dados:** MySQL
- **Mapas:** OpenStreetMap tiles + Nominatim (geocoding)
- **Outras:** Composer, Blade Templates

## 📦 Pré-requisitos

Antes de executar a aplicação, verifique-se de ter instalado:

- PHP 8.2 ou superior
- Composer
- MySQL
- Node.js (opcional, para build de assets)
- XAMPP/WAMP ou ambiente similar (opcional)

## 🚀 Instalação e Configuração

Siga estes passos para configurar o projeto:

1. **Clone/Crie o projeto:**
   ```bash
   compositor create-project laravel/laravel laravel-maps-app
   cd laravel-maps-app
   ```

2. **Configure o ambiente:**
   ```bash
   copy .
   ​
   ​

​
   ​
   ​
   ​
   ​
   ​
   ​
   ​
   ​

​dados:**
   ```sql
   CRIAR BANCO DE DADOS laravel_maps_app CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```

5. **Execute as migrations:**
   ```bash
   php artisan migrate
   ```

6. **Execute a aplicação:**
   ```bash
   php artisan serve
   ```

## 🗺️ Estrutura do Banco de Dados

A tabela `locations` contém:
- `id` (chave primária)
- `name` (string)
- `description` (texto, anulável)
- `latitude` (decimal 10,8)
- `longitude` (decimal 11,8)
- `address` (string, anulável)
- `category` (string, anulável)
- `timestamps`

## 🌐 Pontos de extremidade da API

A API RESTful está disponível em `/api/locations`:

- `GET /api/locations` - Lista todas as localizações
- `POST /api/locations` - Cria uma nova localização
- `GET /api/locations/{id}` - Mostra uma localização específica
- `PUT /api/locations/{id}` - Atualiza uma localização
- `DELETE /api/locations/{id}` - Exclui uma localização

## 📍 Uso do OpenStreetMap

### Tiles do OSM
Uma aplicação utiliza tiles públicos do OpenStreetMap:
```javascript
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    atribuição: '© OpenStreetMap contribuidores'
}).addTo(map);
```

### Políticas de Uso
- ✅ Atribuição visível "© OpenStreetMap contribuidores"
- ✅ Uso educacional/baixo tráfego permitido
- ❌ Uso intensivo requer tile server próprio

### Geocoding com Nominatim
Para uso de geocoding (conversão endereço↔coordenadas):
- Use a instância pública com moderação
- Identifique requests com User-Agent perigosa
Considere - cache para consultas repetidas

## 🎨 Views e Layout

### Estrutura de Views
- `layouts/app.blade.php` - Layout principal
- `locations/index.blade.php` - Lista e mapa principal
- `locations/create.blade.php` - Formulário de criação
- `locations/edit.blade.php` - Formulário de edição
- `locations/show.blade.php` - Detalhes da localização

### Funcionalidades do Mapa
- **Create/Edit:** Clique no mapa para definir definições
- **Index:** Exibe todos os marcadores com pop-ups informativos
- **Mostrar:** Foca no marcador específico com pop-up aberto

## ⚠️ Solução de Problemas Comuns

### Erros de Banco de Dados
- **1045 Acesso negado:** Verifique usuário/senha no `.env`
- **1049 Banco de dados desconhecido:** Confirme se o banco foi criado

### Problemas com Mapas
- **Tiles não carregam:** verifique conexão internet e URL dos tiles
- **Marcadores não aparentes:** verifique console do navegador

### Problemas com API
- **Erros Nominatim:** Verifique User-Agent e limites de requisições

## 🔧 Comandos Artisan Úteis

```bash
# Criar migração
php artesão make:migration create_locations_table

# Executar migrações
php artesão migram

# Criar controlador
php artesão make:controller LocationController --resource

# Criar API controlador
php artesão make:controller Api/LocationController

# Gerar chave da aplicação
php artesão key:generate
```

## 📚 Referências e Links Úteis

- [Início rápido do folheto]( https://leafletjs.com/examples/quick-start/ )
- [Referência da API do folheto]( https://leafletjs.com/reference.html )
- [Política de uso do bloco OSM]( https://operations.osmfoundation.org/policies/tiles/ )
- [Política de uso do Nominatim]( https://operações.osmfoundation.org/policies/nominatim/ )
- [Documentação Nominatim]( https://nominatim.org/ )
- [OSM Copyright]( https://www.openstreetmap.org/copyright )

## 📄 Licença

Este projeto é para fins educacionais. Ao usar o OpenStreetMap, respeite a [licença ODbL]( https://www.openstreetmap.org/copyright ) e as políticas de uso dos serviços.

## 👥 Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para:
- Reportar problemas
- Sugerir novas funcionalidades
- Enviar pull requests

---

**Nota:** Para uso em produção com alto tráfego, considere:
- Hospedar seu próprio servidor de blocos
- Configurar uma instância própria do Nominatim
- Implementar cache adequado
- Utilizar CDN para assets estáticos
