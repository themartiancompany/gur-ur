# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_os="$( \
  uname \
    -o)"
if [[ "${_os}" == "GNU/Linux" ]]; then
  _github_cli="github-cli"
elif [[ "${_os}" == "Android" ]]; then
  _github_cli="gh"
fi
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_git_http_host" ]]; then
  _git_http_host="gitlab"
fi
if [[ ! -v "_archive_format" ]]; then
  _archive_format="tar.gz"
  if [[ "${_git_http_host}" == "github" ]]; then
    _archive_format="zip"
  fi
fi
if [[ ! -v "_docs" ]]; then
  _docs="true"
fi
_node="nodejs"
_py="python"
_proj="hip"
_pkg=gur
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${pkgbase}-docs"
  )
fi
pkgver="0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.1.1"
_commit="159ba217e491dba58964ebc128bd7991abe04201"
_evm_gnupg_ver="0.0.0.0.0.0.0.0.1.1.1"
pkgrel=1
_pkgdesc=(
  "Ur application store Github"
  "and Gitlab HTTP mirrors"
  "management tool."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://${_git_http_host}.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_pkg}"
license=(
  'AGPL3'
)
depends=(
  "curl"
  "evm-gnupg>=${_evm_gnupg_ver}"
  "${_github_cli}"
  "gl-dl"
  "jq"
  "libcrash-bash"
  "${_py}-pygithub"
)
_gur_docs_optdepends=(
  "${_pkg}-docs:"
    "Gur"
    "documentation"
    "and manuals."
)
_gur_docs_ref_optdepends+=(
 "${_pkg}:"
   "The package this documentation"
   "package pertains to."
)
optdepends=(
  "${_gur_docs_optdepends[*]}"
)
if [[ "${_os}" == 'Android' ]]; then
  optdepends+=(
  )
fi
makedepends=(
  'make'
  "${_py}-docutils"
)
checkdepends=(
  "shellcheck"
)
group=(
  "${_proj}"
)
source=(
 "COPYING"
)
sha256sums=(
  "0d96a4ff68ad6d4b6f1f30f713b18d5184912ba8dd389f86aa7710db079abcb0"
)
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_sum="4a405975894967fbe834cdf042ca8864c4ec5c532df32ed25705be4a30b3e39c"
_sig_sum="3146165ec481cfec819d4587f1492c2611c6eb774b16d6231b4f570d58963d03"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarname}.tar.gz::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarname}.tar.gz.sig::${_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_src}"
  _sum="${_sum}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/${_commit}.tar.gz"
    _sum="${_sum}"
  fi
fi
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  # Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package_gur() {
  local \
    _make_opts=()
  _make_opts+=(
    PREFIX="/usr"
    DESTDIR="${pkgdir}"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
  install \
    -Dm644 \
    "${srcdir}/COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_gur-docs() {
  local \
    _make_opts=()
  pkgdesc="${pkgdesc} (documentation)"
  depends=()
  optdepends=(
    "${_gur_docs_ref_optdepends[*]}"
  )
  provides=()
  _make_opts+=(
    PREFIX="/usr"
    DESTDIR="${pkgdir}"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-doc \
    install-man
  install \
    -Dm644 \
    "${srcdir}/COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim: ft=sh syn=sh et
