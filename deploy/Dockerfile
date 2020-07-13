FROM kong:2.1

ENV KONG_PLUGINS=bundled,kong-spec-expose,oidc
USER root
# install Kong's Spec Expose plugin
RUN luarocks install kong-spec-expose

# install kong-oidc plugin from https://github.com/nokia/kong-oidc/
RUN luarocks install kong-oidc
USER kong