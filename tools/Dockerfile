FROM        ocaml/opam2:debian-10-ocaml-4.07
MAINTAINER  Christian Lindig <christian.lindig@citrix.com>

COPY --chown=opam:opam . /tmp/xs-opam

RUN sudo apt-get update
RUN sudo apt-get install -qq -yy hwdata libdlm-dev libffi-dev libgmp-dev \
                                 libnl-3-200 libnl-route-3-200 libpam-dev \
                                 libpci-dev libssl-dev libsystemd-dev libxen-dev \
                                 libxxhash-dev libxxhash0 m4 perl pkg-config python
RUN opam repo remove --all default \
 && opam repo add xs-opam file:///tmp/xs-opam \
 && opam depext -y xs-toolstack \
 && opam install xs-toolstack
