<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "cd973a4e381337c6a3ac2443e7548e63",
  "translation_date": "2025-07-14T02:28:30+00:00",
  "source_file": "05-AdvancedTopics/mcp-scaling/README.md",
  "language_code": "ko"
}
-->
## 수직 확장 및 자원 최적화

수직 확장은 단일 MCP 서버 인스턴스를 최적화하여 더 많은 요청을 효율적으로 처리하는 데 중점을 둡니다. 이는 설정을 세밀하게 조정하고, 효율적인 알고리즘을 사용하며, 자원을 효과적으로 관리함으로써 달성할 수 있습니다. 예를 들어, 스레드 풀, 요청 타임아웃, 메모리 한도를 조정하여 성능을 향상시킬 수 있습니다.

수직 확장과 자원 관리를 위해 MCP 서버를 최적화하는 방법의 예를 살펴보겠습니다.

## 분산 아키텍처

분산 아키텍처는 여러 MCP 노드가 함께 작동하여 요청을 처리하고, 자원을 공유하며, 중복성을 제공하는 방식을 말합니다. 이 접근법은 노드들이 분산 시스템을 통해 소통하고 조율할 수 있게 하여 확장성과 장애 허용성을 높입니다.

Redis를 사용해 조율하는 분산 MCP 서버 아키텍처를 구현하는 예를 살펴보겠습니다.

## 다음 단계

- [5.8 Security](../mcp-security/README.md)

**면책 조항**:  
이 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 최선을 다하고 있으나, 자동 번역에는 오류나 부정확한 부분이 있을 수 있음을 유의하시기 바랍니다. 원문은 해당 언어의 원본 문서가 권위 있는 출처로 간주되어야 합니다. 중요한 정보의 경우 전문적인 인간 번역을 권장합니다. 본 번역 사용으로 인해 발생하는 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.