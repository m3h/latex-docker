FROM ubuntu:latest

ARG TEXLIVE_PROFILE="/texlive.profile"
ARG INSTALL_TL_URL="https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz"
ARG LATEX_INSTALL_DIR=/tmp/latex_install/
RUN mkdir "${LATEX_INSTALL_DIR}"

COPY texlive.profile "${TEXLIVE_PROFILE}"

# curl is required to download the install-tl script
# libtest-pod-perl is required to run the install-tl script
RUN apt-get update && apt-get install -y \
	curl \
	libtest-pod-perl

RUN curl "${INSTALL_TL_URL}" --location --output "${LATEX_INSTALL_DIR}/install-tl.tar.gz" \
	&& tar xaf "${LATEX_INSTALL_DIR}/install-tl.tar.gz" --directory="${LATEX_INSTALL_DIR}" \
	&& rm -rf "${LATEX_INSTALL_DIR}/install-tl.tar.gz" \
	&& mv "${LATEX_INSTALL_DIR}"/install-tl-* "${LATEX_INSTALL_DIR}/install-tl"

RUN "${LATEX_INSTALL_DIR}/install-tl/install-tl" \
	--profile="${TEXLIVE_PROFILE}"

ARG LATEX_UPDATE_TIME=unknown
RUN tlmgr update --all \
	&& echo "${LATEX_UPDATE_TIME}" >> /latex_update_time
