tink_module(signature)

tink_cc_library(
  NAME public_key_verify_wrapper
  SRCS
    public_key_verify_wrapper.cc
    public_key_verify_wrapper.h
  DEPS
    tink::core::crypto_format
    tink::core::primitive_set
    tink::core::primitive_wrapper
    tink::core::public_key_verify
    tink::subtle::subtle_util_boringssl
    tink::util::status
    tink::util::statusor
    tink::proto::tink
    absl::strings
)

tink_cc_library(
  NAME public_key_verify_factory
  SRCS
    public_key_verify_factory.cc
    public_key_verify_factory.h
  DEPS
    tink::signature::public_key_verify_wrapper
    tink::core::key_manager
    tink::core::keyset_handle
    tink::core::primitive_set
    tink::core::public_key_verify
    tink::core::registry
    tink::util::status
    tink::util::statusor
    absl::base
)

tink_cc_library(
  NAME public_key_sign_wrapper
  SRCS
    public_key_sign_wrapper.cc
    public_key_sign_wrapper.h
  DEPS
    tink::core::crypto_format
    tink::core::primitive_set
    tink::core::primitive_wrapper
    tink::core::public_key_sign
    tink::subtle::subtle_util_boringssl
    tink::util::status
    tink::util::statusor
    tink::proto::tink
    absl::strings
)

tink_cc_library(
  NAME public_key_sign_factory
  SRCS
    public_key_sign_factory.cc
    public_key_sign_factory.h
  DEPS
    tink::signature::public_key_sign_wrapper
    tink::core::key_manager
    tink::core::keyset_handle
    tink::core::primitive_set
    tink::core::public_key_sign
    tink::core::registry
    tink::util::status
    tink::util::statusor
    absl::base
)

tink_cc_library(
  NAME signature_key_templates
  SRCS
    signature_key_templates.cc
    signature_key_templates.h
  DEPS
    tink::subtle::subtle_util_boringssl
    tink::util::constants
    tink::proto::common
    tink::proto::ecdsa
    tink::proto::ed25519
    tink::proto::rsa_ssa_pkcs1
    tink::proto::rsa_ssa_pss
    tink::proto::tink
    crypto
    absl::memory
    absl::strings
)

tink_cc_library(
  NAME ecdsa_sign_key_manager
  SRCS
    ecdsa_sign_key_manager.cc
    ecdsa_sign_key_manager.h
  DEPS
    tink::signature::ecdsa_verify_key_manager
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_sign
    tink::core::registry
    tink::subtle::ecdsa_sign_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::enums
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::proto::common
    tink::proto::ecdsa
    tink::proto::tink
    absl::memory
    absl::strings
)

tink_cc_library(
  NAME ecdsa_verify_key_manager
  SRCS
    ecdsa_verify_key_manager.cc
    ecdsa_verify_key_manager.h
  DEPS
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_verify
    tink::core::registry
    tink::subtle::ecdsa_verify_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::enums
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::proto::common
    tink::proto::ecdsa
    tink::proto::tink
)

tink_cc_library(
  NAME ed25519_sign_key_manager
  SRCS
    ed25519_sign_key_manager.cc
    ed25519_sign_key_manager.h
  DEPS
    tink::signature::ed25519_verify_key_manager
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_sign
    tink::subtle::ed25519_sign_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::enums
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::util::validation
    tink::proto::ed25519
    tink::proto::empty
    tink::proto::tink
    absl::memory
    absl::strings
)

tink_cc_library(
  NAME ed25519_verify_key_manager
  SRCS
    ed25519_verify_key_manager.cc
    ed25519_verify_key_manager.h
  DEPS
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_verify
    tink::subtle::ed25519_verify_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::util::validation
    tink::proto::ed25519
    absl::strings
)

tink_cc_library(
  NAME sig_util
  SRCS
    sig_util.cc
    sig_util.h
  DEPS
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::util::status
)

tink_cc_library(
  NAME rsa_ssa_pkcs1_sign_key_manager
  SRCS
    rsa_ssa_pkcs1_sign_key_manager.cc
    rsa_ssa_pkcs1_sign_key_manager.h
  DEPS
    tink::signature::rsa_ssa_pkcs1_verify_key_manager
    tink::signature::sig_util
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_sign
    tink::core::registry
    tink::subtle::rsa_ssa_pkcs1_sign_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::enums
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::proto::common
    tink::proto::rsa_ssa_pkcs1
    tink::proto::tink
    absl::memory
    absl::strings
)

tink_cc_library(
  NAME rsa_ssa_pkcs1_verify_key_manager
  SRCS
    rsa_ssa_pkcs1_verify_key_manager.cc
    rsa_ssa_pkcs1_verify_key_manager.h
  DEPS
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_verify
    tink::core::registry
    tink::subtle::rsa_ssa_pkcs1_verify_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::enums
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::proto::common
    tink::proto::rsa_ssa_pkcs1
    tink::proto::tink
)

tink_cc_library(
  NAME rsa_ssa_pss_sign_key_manager
  SRCS
    rsa_ssa_pss_sign_key_manager.cc
    rsa_ssa_pss_sign_key_manager.h
  DEPS
    tink::signature::rsa_ssa_pss_verify_key_manager
    tink::signature::sig_util
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_sign
    tink::core::registry
    tink::subtle::rsa_ssa_pss_sign_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::enums
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::proto::common
    tink::proto::rsa_ssa_pss
    tink::proto::tink
    absl::memory
    absl::strings
)

tink_cc_library(
  NAME rsa_ssa_pss_verify_key_manager
  SRCS
    rsa_ssa_pss_verify_key_manager.cc
    rsa_ssa_pss_verify_key_manager.h
  DEPS
    tink::core::key_manager
    tink::core::key_manager_base
    tink::core::public_key_verify
    tink::core::registry
    tink::subtle::rsa_ssa_pss_verify_boringssl
    tink::subtle::subtle_util_boringssl
    tink::util::enums
    tink::util::errors
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::proto::common
    tink::proto::rsa_ssa_pss
    tink::proto::tink
)

tink_cc_library(
  NAME public_key_sign_catalogue
  SRCS
    public_key_sign_catalogue.cc
    public_key_sign_catalogue.h
  DEPS
    tink::signature::ecdsa_sign_key_manager
    tink::signature::ed25519_sign_key_manager
    tink::signature::rsa_ssa_pkcs1_sign_key_manager
    tink::signature::rsa_ssa_pss_sign_key_manager
    tink::core::catalogue
    tink::core::key_manager
    tink::core::public_key_sign
    tink::util::status
    tink::util::statusor
)

tink_cc_library(
  NAME public_key_verify_catalogue
  SRCS
    public_key_verify_catalogue.cc
    public_key_verify_catalogue.h
  DEPS
    tink::signature::ecdsa_verify_key_manager
    tink::signature::ed25519_verify_key_manager
    tink::signature::rsa_ssa_pkcs1_verify_key_manager
    tink::signature::rsa_ssa_pss_verify_key_manager
    tink::core::catalogue
    tink::core::key_manager
    tink::core::public_key_verify
    tink::util::status
    tink::util::statusor
    absl::str_format
)

tink_cc_library(
  NAME signature_config
  SRCS
    signature_config.cc
    signature_config.h
  DEPS
    tink::signature::public_key_sign_catalogue
    tink::signature::public_key_verify_catalogue
    tink::core::config
    tink::core::registry
    tink::util::status
    tink::proto::config
    absl::memory
)

# tests

tink_cc_test(
  NAME public_key_verify_wrapper_test
  SRCS public_key_verify_wrapper_test.cc
  DEPS
    tink::signature::public_key_verify_wrapper
    tink::core::primitive_set
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::util::status
    tink::util::test_util
    tink::proto::tink
)

tink_cc_test(
  NAME public_key_verify_factory_test
  SRCS public_key_verify_factory_test.cc
  DEPS
    tink::signature::ecdsa_verify_key_manager
    tink::signature::public_key_verify_factory
    tink::signature::signature_config
    tink::core::config
    tink::core::keyset_handle
    tink::core::public_key_verify
    tink::core::registry
    tink::util::keyset_util
    tink::util::status
    tink::util::test_util
    tink::proto::ecdsa
    tink::proto::tink
)

tink_cc_test(
  NAME public_key_sign_wrapper_test
  SRCS public_key_sign_wrapper_test.cc
  DEPS
    tink::signature::public_key_sign_wrapper
    tink::core::crypto_format
    tink::core::primitive_set
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::util::status
    tink::util::test_util
    tink::proto::tink
)

tink_cc_test(
  NAME public_key_sign_factory_test
  SRCS public_key_sign_factory_test.cc
  DEPS
    tink::signature::ecdsa_sign_key_manager
    tink::signature::public_key_sign_factory
    tink::signature::signature_config
    tink::core::config
    tink::core::keyset_handle
    tink::core::public_key_sign
    tink::core::registry
    tink::util::keyset_util
    tink::util::status
    tink::util::test_util
    tink::proto::ecdsa
    tink::proto::tink
)

tink_cc_test(
  NAME ecdsa_verify_key_manager_test
  SRCS ecdsa_verify_key_manager_test.cc
  DEPS
    tink::signature::ecdsa_sign_key_manager
    tink::signature::ecdsa_verify_key_manager
    tink::core::config
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::core::registry
    tink::util::status
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::ecdsa
    tink::proto::tink
)

tink_cc_test(
  NAME ed25519_verify_key_manager_test
  SRCS ed25519_verify_key_manager_test.cc
  DEPS
    tink::signature::ed25519_sign_key_manager
    tink::signature::ed25519_verify_key_manager
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::core::registry
    tink::util::status
    tink::util::statusor
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::ed25519
    tink::proto::empty
    tink::proto::tink
)

tink_cc_test(
  NAME rsa_ssa_pkcs1_verify_key_manager_test
  SRCS rsa_ssa_pkcs1_verify_key_manager_test.cc
  DEPS
    tink::signature::rsa_ssa_pkcs1_verify_key_manager
    tink::core::config
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::core::registry
    tink::util::status
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::rsa_ssa_pkcs1
    tink::proto::tink
    absl::strings
)

tink_cc_test(
  NAME rsa_ssa_pss_verify_key_manager_test
  SRCS rsa_ssa_pss_verify_key_manager_test.cc
  DEPS
    tink::signature::rsa_ssa_pss_verify_key_manager
    tink::core::config
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::core::registry
    tink::util::status
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::rsa_ssa_pss
    tink::proto::tink
    absl::strings
)

tink_cc_test(
  NAME ecdsa_sign_key_manager_test
  SRCS ecdsa_sign_key_manager_test.cc
  DEPS
    tink::signature::ecdsa_sign_key_manager
    tink::signature::ecdsa_verify_key_manager
    tink::signature::signature_key_templates
    tink::core::config
    tink::core::public_key_sign
    tink::core::registry
    tink::aead::aead_key_templates
    tink::aead::aes_gcm_key_manager
    tink::util::status
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::ecdsa
    tink::proto::tink
)

tink_cc_test(
  NAME ed25519_sign_key_manager_test
  SRCS ed25519_sign_key_manager_test.cc
  DEPS
    tink::signature::ed25519_sign_key_manager
    tink::signature::ed25519_verify_key_manager
    tink::signature::signature_key_templates
    tink::core::public_key_sign
    tink::core::registry
    tink::aead::aead_key_templates
    tink::aead::aes_gcm_key_manager
    tink::util::protobuf_helper
    tink::util::status
    tink::util::statusor
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::ed25519
    tink::proto::empty
    tink::proto::tink
)

tink_cc_test(
  NAME rsa_ssa_pkcs1_sign_key_manager_test
  SRCS rsa_ssa_pkcs1_sign_key_manager_test.cc
  DEPS
    tink::signature::rsa_ssa_pkcs1_sign_key_manager
    tink::signature::rsa_ssa_pkcs1_verify_key_manager
    tink::signature::signature_key_templates
    tink::core::config
    tink::core::public_key_sign
    tink::core::registry
    tink::aead::aead_key_templates
    tink::aead::aes_gcm_key_manager
    tink::subtle::subtle_util_boringssl
    tink::util::status
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::rsa_ssa_pkcs1
    tink::proto::tink
    crypto
)

tink_cc_test(
  NAME rsa_ssa_pss_sign_key_manager_test
  SRCS rsa_ssa_pss_sign_key_manager_test.cc
  DEPS
    tink::signature::rsa_ssa_pss_sign_key_manager
    tink::signature::rsa_ssa_pss_verify_key_manager
    tink::signature::signature_key_templates
    tink::core::config
    tink::core::public_key_sign
    tink::core::registry
    tink::aead::aead_key_templates
    tink::aead::aes_gcm_key_manager
    tink::subtle::subtle_util_boringssl
    tink::util::status
    tink::util::test_util
    tink::proto::aes_eax
    tink::proto::common
    tink::proto::rsa_ssa_pss
    tink::proto::tink
    crypto
)

tink_cc_test(
  NAME public_key_sign_catalogue_test
  SRCS public_key_sign_catalogue_test.cc
  DEPS
    tink::signature::public_key_sign_catalogue
    tink::core::catalogue
    tink::util::status
    tink::util::statusor
)

tink_cc_test(
  NAME public_key_verify_catalogue_test
  SRCS public_key_verify_catalogue_test.cc
  DEPS
    tink::signature::public_key_verify_catalogue
    tink::core::catalogue
    tink::util::status
    tink::util::statusor
)

tink_cc_test(
  NAME signature_config_test
  SRCS signature_config_test.cc
  DEPS
    tink::signature::signature_config
    tink::signature::signature_key_templates
    tink::core::catalogue
    tink::core::config
    tink::core::keyset_handle
    tink::core::public_key_sign
    tink::core::public_key_verify
    tink::core::registry
    tink::util::status
    tink::util::test_matchers
    tink::util::test_util
    absl::memory
)

tink_cc_test(
  NAME signature_key_templates_test
  SRCS signature_key_templates_test.cc
  DEPS
    tink::signature::ecdsa_sign_key_manager
    tink::signature::ed25519_sign_key_manager
    tink::signature::rsa_ssa_pkcs1_sign_key_manager
    tink::signature::rsa_ssa_pss_sign_key_manager
    tink::signature::signature_key_templates
    tink::subtle::subtle_util_boringssl
    tink::proto::common
    tink::proto::ecdsa
    tink::proto::ed25519
    tink::proto::empty
    tink::proto::rsa_ssa_pkcs1
    tink::proto::rsa_ssa_pss
    tink::proto::tink
    crypto
)