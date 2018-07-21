<!DOCTYPE html>
<html>
<head>
  <title>Twitter</title>
  <%= csrf_meta_tags %>

  <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
  <%= stylesheet_link_tag "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" %>
  <%= javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>
</head>

<body>
  <% if flash[:notice] %>
  <div class="notification is-primary global-notification">
    <p class="notice"><%= notice %></p>
  </div>
  <% end %>
  <% if flash[:alert] %>
  <div class="notification is-danger global-notification">
    <p class="alert"><%= alert %></p>
  </div>
  <% end %>
  <nav class="navbar is-info">
    <div class="navbar-brand">
      <%= link_to root_path, class:"navbar-item" do %>
      <h1 class="title is-5">Twitter</h1>
      <% end %>
      <div class="navbar-burger burger" data-target="navbarExample"> 
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
    <div id="navbarExample" class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <div class="field is-grouped">
            <p class="control">
              <%= link_to 'New Tweeet', root_path, class: "button is-info is-inverted" %>
            </p> 
            <% if user_signed_in? %>
            <p class="control">
              <%= link_to current_user.name, edit_user_registration_path, class: "button is-info" %>
            </p>
            <p>
              <%= link_to "Logout", destroy_user_session_path, method: :delete, class: "button is-info" %>
            </p>
            <% else %>
            <p class="control">
              <%= link_to "Sign In", new_user_session_path, class: "button is-info" %>
            </p>
            <p class="control">
              <%= link_to "Sign Up", new_user_registration_path, class: "button is-info" %>
            </p>
            <% end %>
          </div>
        </div>
      </div>
    </div>
  </nav>
  <%= yield %>
</body>
</html>
