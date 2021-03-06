# SASS Bootstrap navbar

## HTML template

Start by copying our navbar HTML template

```html
<nav class="navbar navbar-default navbar-fixed-top navbar-wagon" role="navigation">
  <div class="container-fluid">
    <!-- Brand and toggle get grouped for better mobile display -->
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="#">
        <img src="images/logo.png" id="logo" alt="">
      </a>
    </div>

    <!-- Collect the nav links, forms, and other content for toggling -->
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">


      <ul class="nav navbar-nav navbar-right">
        <li><a href="#"><i class="fa fa-envelope-o"></i> Contact</a></li>
        <li class="dropdown">
          <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-expanded="false"><img src="http://placehold.it/30x30" id="profile-pic" alt="">Follow-us <span class="caret"></span></a>
          <ul class="dropdown-menu" role="menu">
            <li><a href="https://www.facebook.com/lewagonformation"><i class="fa fa-facebook-square"></i> Facebook</a></li>
            <li><a href="https://twitter.com/lewagonparis"><i class="fa fa-twitter-square"></i> Twitter</a></li>
          </ul>
        </li>
        <li><a href="#" class="btn btn-primary" id="nav-btn">Publish an announce</a></li>
      </ul>
    </div><!-- /.navbar-collapse -->
  </div><!-- /.container-fluid -->
</nav>
```

Of course, you have to find your own logo image and replace the profile picture url by your profile picture.


### Respect our classes

For our design to work you must have the following HTML elements:

- your `nav` should have an additional **`class="navbar-wagon"`**
- your logo should be an image and have a **`id="logo"`**
- your profile picture should have a **`id="profile-pic"`**
- you button should have a **`id="nav-btn"`**


## SASS template

Our `navbar.scss` implements style rules on the `.wagon-navbar` class. Herebelow we detail the purpose of each sass variable in `navbar.scss`.

### Wagon-navbar Sass variable

#### Navbar general appearance

Change your navbar background and text color

```scss
$color: black;
$bg: white;
```

Change the height of its content and its horizontal and vertical paddings.

```scss
$height: 40px;
$vertical-padding: 10px;
$horizontal-padding: 20px;
```

Customize your navbar bottom border if you want to:

```scss
$border-bottom-width: 0;
$border-bottom-color: transparent;
```

#### Navbar button style

Our `navbar.scss` gives you lot of flexibility for pimping your navbar button.

```scss
$btn-height: 40px;
$btn-bg: lightgrey;
$btn-color: black;
$btn-horizontal-padding: 10px;
$btn-top-border-width: 0;
$btn-top-border-color: transparent;
$btn-right-border-width: 0;
$btn-right-border-color: transparent;
$btn-bottom-border-width: 3px;
$btn-bottom-border-color: grey;
$btn-left-border-width: 0;
$btn-left-border-color: transparent;
```

#### Profile picture style

You can also pimp your navbar profile picture by changing its radius and its border

```scss
// Set your profile picture
$profile-radius: 20%;
$profile-border-color: white;
$profile-border-width: 2px;
```


## Integration in Rails

### Rails assets

In Rails, the integration is easy if you have installed `sass-rails` and `bootstrap-sass` gems. You can just add the `navbar.scss` file to your Rails stylesheets, and then import this file in `application.css.scss`


```scss
//application.css.scss

// "bootstrap-sass" imports
@import "bootstrap-sprockets";
@import "bootstrap";

// Import our navbar.scss after bootstrap
@import "navbar";
```

Here you go!

### ERB template

Don't forget to inject the `erb` parts using rails helpers carefully, for example:

```erb
<nav class="navbar navbar-default navbar-fixed-top navbar-wagon" role="navigation">
  <div class="container-fluid">
    <!-- Brand and toggle get grouped for better mobile display -->
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="#">
        <%= image_tag "logo.png", id: "logo" %>
      </a>
    </div>

    <!-- Collect the nav links, forms, and other content for toggling -->
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      <ul class="nav navbar-nav navbar-right">
        <li>
          <%= link_to "/users/1/messages" do %>
            <i class="fa fa-envelope-o"></i> Messages
          <% end %>
        </li>
        <li class="dropdown">
          <%= link_to "#", {class: "dropdown-toggle", "data-toggle" => "dropdown", "role" => "button", "aria-expanded" => "false"} do %>
            <%= image_tag "http://placehold.it/30x30", id: "profile-pic" %>
            Profile <span class="caret"></span>
          <% end %>
          <ul class="dropdown-menu" role="menu">
            <li>
              <%= link_to "/users/1" do %>
                <i class="fa fa-user"></i> Profile
              <% end %>
            </li>
            <li>
              <%= link_to "/users/1/flats" do %>
                <i class="fa fa-home"></i> Flats
              <% end %>
            </li>
            <li>
              <%= link_to "/signout" do %>
                <i class="fa fa-sign-out"></i> Sign Out
              <% end %>
            </li>
          </ul>
        </li>
        <li>
          <%= link_to "/flats/new", class: "btn btn-primary", id: "nav-btn" do %>
            Publish an announce
          <% end %>
        </li>
      </ul>
    </div><!-- /.navbar-collapse -->
  </div><!-- /.container-fluid -->
</nav>
```

## Contribute, share your masterpiece!

Feel free to contribute to this project with pull requests, and to share with us your navbar masterpieces.

- Twitter: https://twitter.com/lewagonparis
- Facebook: https://facebook.com/lewagonformation
- Website: http://lewagon.org

Peace!
