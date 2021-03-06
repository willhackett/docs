---
url: /identityproviders
description: Auth0 is an identity hub that supports the many authentication providers listed here.
topics:
  - connections
contentType: 
    - index
    - reference
useCase:
  - customize-connections
  - add-idp
---
# Connections

A connection is the relationship between Auth0 and a source of users. Auth0 sits between your application and its sources of users, which adds a level of abstraction so your application is isolated from any changes to and idiosyncrasies of each source's implementation.

You can configure any number of connections for your applications to use in the Auth0 Dashboard. To view all the connections that you have configured or create new ones, see [View Connections](/dashboard/guides/connections/view-connections).

By default, Auth0 automatically syncs user profile data with each user login, thereby ensuring that changes made in the connection source are automatically updated in Auth0. You can [optionally disable this synchronization](/dashboard/guides/connections/configure-connection-sync) to allow for updating profile attributes from your application.

# Identity Providers Supported by Auth0

An Identity Provider is a server that can provide identity information to other servers. For example, Google is an Identity Provider. If you log in to a site using your Google account, then a Google server will send your identity information to that site.

Auth0 is an identity hub that supports many Identity Providers using various protocols (like <dfn data-key="openid">OpenID Connect (OIDC)</dfn>, <dfn data-key="security-assertion-markup-language">SAML</dfn>, [WS-Federation](/protocols/ws-fed), and more).

Auth0 sits between your app and the Identity Provider that authenticates your users. This adds a level of abstraction so your app is isolated from any changes to and idiosyncrasies of each provider's implementation.

The relationship between Auth0 and any of these authentication providers is referred to as a **connection**. Auth0 supports [Social](#social), [Enterprise](#enterprise), [Database](#database-and-custom-connections) and <dfn data-key="passwordless">[Passwordless](#passwordless)</dfn> connections.

## Social

Auth0 supports the following social providers out of the box. You can also use any [OAuth2 Authorization Server](/connections/social/oauth2).

<% var socialConnections = cache.find('articles/connections/social', {sort: 'index'}); %>
<%= include('./_connections', { connections: socialConnections }) %>

## Enterprise

<% var enterpriseConnections = cache.find('articles/connections/enterprise', {sort: 'index'}); %>
<%= include('./_connections', { connections: enterpriseConnections }) %>

## Legal Identities

Through our partner, Criipto, we offer a growing range of government and bank identities tied to legal persons. 

<% var criiptoConnections = cache.find('articles/connections/criipto', {sort: 'index'}); %>
<%= include('./_connections', { connections: criiptoConnections }) %>

If the one you need isn't found here, we suggest getting in touch with [Criipto](https://criipto.com).

## Database and Custom Connections

If you want to create your own user store, instead of using external identity providers like Google or Facebook, you can use a Database Connection. This way you can authenticate users with an email or username and a password. The credentials can be securely stored either in the Auth0 user store or in your own database.

You can create any number of custom fields and store this information as part of the `user_metadata`. You can easily import users from a legacy user store, enable or disable sign ups, configure your password policy, or enable <dfn data-key="multifactor-authentication">multi-factor authentication (MFA)</dfn>.

For more details, refer to the [Database Connections](/connections/database) documentation.

## Passwordless

Full documentation on Passwordless authentication can be found at the links below:

<ul>
<li><a href="/connections/passwordless">Passwordless Authentication Overview</a></li>
<% cache.find('articles/connections/passwordless', {sort: 'connection'}).forEach(article => { %>
  <% if (article.connection) { %>
    <li>
      <% if (article.public === false) { %>
        <%- article.connection %>
      <% } else { %>
        <a href="<%- article.url %>"><%- article.connection %></a>
      <% } %>
    </li>
  <% } %>
<% }); %>
</ul>
