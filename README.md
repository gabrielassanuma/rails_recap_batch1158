## Rails Recap Class - Batch 1156


## Create local setup

Inside your code folder:

```bash
  mkdir rails_recap_batch1158
  cd rails_recap_batch1158
```

Set up Le Wagon minimal rails template

```bash
  rails new \
  -d postgresql \
  -j webpack \
  -m https://raw.githubusercontent.com/lewagon/rails-templates/master/minimal.rb \
  rails_recap_batch1158
```

Create repo and push it to github
```bash
  git init
  git add .
  git commit -m "First commit"
  gh repo create --public --source=.
```

Check your repo on browser
```bash
  gh repo view --web
```

## Model

We NEVER 🙅🏻‍♂️ work on MASTER!🙅🏽‍♀️

Create a branch before move on
```bash
  git checkout -b model-creation
```

Create model Post
```bash
  rails g model Post title content
```

Generate 5 Posts using seed.rb

Start by including faker in your Gemfile
```bash
   gem 'faker'
```

Run bundle install
```bash
   bundle install
```

On your seed.rd
```bash
   require 'faker'

  puts "Dropping data..."
  puts "Creating new seed"
  5.times do | index |
    puts "creating #{index + 1} Post"
    Post.create(title: Faker::Book.title, content: Faker::Lorem.paragraph)
    puts "#{index + 1} Post created!"
  end
```

Check Posts on console
```bash
   rails console
```

Push changes to github
```bash
   ➡️git add .
   git commit -m "post model, schema and seed created"
   gi➡️t push model-creation main
```

## Controller

Always remember...
We NEVER 🙅🏻‍♂️ work on MASTER!🙅🏽‍♀️

Create a branch before move on
```bash
  git checkout -b controller-creation
```

Create Posts controller
```bash
   rails g controller posts
```

Let's add all CRUD actions to Post controller, always follow the flow:
route ➡️ controller#action ➡ view

In your config folder open routes.rb add the path for our first action, index will be our root path also.
```bash
   root "posts#index"
   get "/posts", to: "posts#index"
```

Go to app/controllers/posts and add index function:
```bash
   def index
    @posts = Post.all
  end
```

Go to app/views and create one posts folder, inside it create one file index.html.erb and copy this code:
```bash
  <div class="container">
    <div class="row">
      <div class="col6 my-5 d-flex justify-content-center">
        <h1>I LOVE RAILS ❤️</h1>
      </div>
    </div>
    <div class="cards">
      <% @posts.each do | post | %>
        <div class="card">
          <div class="card-header">
            <%= "Card for post - #{post.id}" %>
          </div>
          <div class="card-body">
            <h5 class="card-title"><%= post.title %></h5>
            <p class="card-text"><%= post.content %></p>
            <a href="#" class="btn btn-light">Go somewhere</a>
          </div>
        </div>
      <% end %>
    </div>
  </div>
```

Go to app/assets/stylesheets create one posts folder, inside it create one file index.sccs and copy this code:
```bash
  .cards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-gap: 18px;
}
```

Don't forget to import it to application.scss ⤵️ ❗️
