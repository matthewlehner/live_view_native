# LiveViewNative

[![Build Status](https://github.com/liveview-native/live_view_native/workflows/Elixir%20CI/badge.svg)](https://github.com/liveview-native/live_view_native/actions) [![Hex.pm](https://img.shields.io/hexpm/v/live_view_native.svg)](https://hex.pm/packages/live_view_native) [![Documentation](https://img.shields.io/badge/documentation-gray)](https://hexdocs.pm/live_view_native)

## About

LiveView Native is a platform for building native applications using [Elixir](https://elixir-lang.org/) and [Phoenix LiveView](https://github.com/phoenixframework/phoenix_live_view). It allows a single LiveView to serve both web and non-web clients by transforming platform-specific template code into native UIs:

```elixir
# lib/my_app_web/live/hello_live.ex
defmodule MyAppWeb.HelloLive do
  use MyAppWeb, :live_view
  use MyAppNative, :live_view
end

# liv/my_app_web/live/hello_live_swiftui.ex
defmodule MyAppWeb.HelloLive.SwiftUI do
  use MyAppNative, [:render_component, format: :swiftui]

  def render(assigns, %{"target" => "watchos"}) do
    ~LVN"""
    <VStack>
      <Text>
        Hello WatchOS!
      </Text>
    </VStack>
    """
  end

  def render(assigns, _interface) do
    ~LVN"""
    <VStack>
      <Text>
        Hello SwiftUI!
      </Text>
    </VStack>
    """
  end
end
```

## Getting started

To get started with LiveView Native, you'll need to have an existing [Phoenix Application](https://hexdocs.pm/phoenix/up_and_running.html) or create a new one.

Add `live_view_native` to your list of dependencies in the `mix.exs` file. In addition to `live_view_native` you may want to include some additional libraries:

```elixir
{:live_view_native, "~> 0.3.0-rc.4"},
{:live_view_native_stylesheet, "~> 0.3.0-rc.4"},
{:live_view_native_swiftui, "~> 0.3.0-rc.4"},
{:live_view_native_live_form, "~> 0.3.0-rc.3"}
```

The versions above may be subject to change, so make sure to check the library documentation for the latest version.
* [LiveView Native Versions](https://hex.pm/packages/live_view_native/versions)
* [LiveView Native Stylesheet Versions](https://hex.pm/packages/live_view_native_stylesheet/versions)
* [LiveView Native SwiftUI Client Versions](https://hex.pm/packages/live_view_native_swiftui/versions)
* [LiveView Native Live Form Versions](https://hex.pm/packages/live_view_native_live_form/versions)

Then run:

```
$ mix lvn.setup
```

and follow the instructions on how to complete the setup process.

## Main Branch

To try out new features or get the latest bugfixes you can also use the `main` branch for LiveView Native dependencies.

```elixir
{:live_view_native, github: "liveview-native/live_view_native", override: true},
{:live_view_native_stylesheet, github: "liveview-native/live_view_native_stylesheet"},
{:live_view_native_swiftui, github: "liveview-native/liveview-client-swiftui"},
{:live_view_native_live_form, github: "liveview-native/liveview-native-live-form"}
```

However, be aware that active changes may make your development experience unstable.

## Native Clients

LiveView Native enables native client frameworks such as the [LiveView Native SwiftUI Client](https://github.com/liveview-native/liveview-client-swiftui) and the [LiveView Native Jetpack Client (In Progress)](https://github.com/liveview-native/liveview-client-jetpack).

### SwiftUI Client

To create your first LiveView Native LiveView, go to the [LiveView Native SwiftUI Client Usage](https://github.com/liveview-native/liveview-client-swiftui?tab=readme-ov-file#usage) guide on GitHub. Alternatively, you can read the [LiveView Native SwiftUI Documentation] where you can find documentation, examples, and interactive Livebook guides. 

### Jetpack (Android) Client

The Jetpack client is in progress. You can follow our progress on the [LiveView Native JetPack Client](https://github.com/liveview-native/liveview-client-jetpack) repository.

## Questions?

Have a question or want some help with LiveView Native?

Check out the `#liveview-native` channel on the [Elixir Lang Slack](https://elixir-lang.slack.com/).