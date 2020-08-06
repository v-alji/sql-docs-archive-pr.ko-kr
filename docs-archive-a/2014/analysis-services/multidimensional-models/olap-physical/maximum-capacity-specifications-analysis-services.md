---
title: 최대 용량 사양 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], maximum number
- objects [Analysis Services], maximum size
ms.assetid: 49fe1673-b908-4c7a-88ff-415efd294d27
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0495ed563585a5b7427655428a257174673fc02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653588"
---
# <a name="maximum-capacity-specifications-analysis-services"></a>최대 용량 사양(Analysis Services)
  다음 표에서는 여러 다른 서버 배포 모드에서 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 구성 요소에 정의된 다양한 개체의 최대 크기 및 개수를 보여 줍니다.  
  
 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
 [다차원 및 데이터 마이닝(DeploymentMode=0)](#bkmk_OLAP)  
  
 [SharePoint(DeploymentMode=1)](#bkmk_sharepoint)  
  
 [테이블 형식(DeploymentMode=2)](#bkmk_vertipaq)  
  
##  <a name="multidimensional-and-data-mining-deploymentmode0"></a><a name="bkmk_OLAP"></a>다차원 및 데이터 마이닝 (DeploymentMode = 0)  
 데이터와 메타데이터가 저장되는 MOLAP 스토리지 모드에서는 파일 크기에 대한 추가적인 물리적 제한이 있습니다. 기본적으로 문자열 저장소 파일의 최대 크기는 4GB입니다. 더 큰 문자열 스토리지 파일이 필요한 경우 다른 문자열 스토리지 아키텍처를 지정할 수 있습니다. 자세한 내용은 [차원 및 파티션에 대 한 문자열 저장소 구성](../configure-string-storage-for-dimensions-and-partitions.md)을 참조 하세요.  
  
|Object|최대 크기/개수|  
|------------|----------------------------|  
|인스턴스의 데이터베이스|2^31-1 = 2,147,483,647|  
|데이터베이스의 차원|2^31-1 = 2,147,483,647|  
|차원의 특성|2^31-1 = 2,147,483,647|  
|차원 특성의 멤버|2^31-1 = 2,147,483,647|  
|차원의 사용자 정의 계층|2^31-1 = 2,147,483,647|  
|사용자 정의 계층 수준|2^31-1 = 2,147,483,647|  
|데이터베이스의 큐브|2^31-1 = 2,147,483,647|  
|큐브의 측정값 그룹|2^31-1 = 2,147,483,647|  
|측정값 그룹의 측정값|2^31-1 = 2,147,483,647|  
|큐브의 계산|2^31-1 = 2,147,483,647|  
|큐브의 KPI|2^31-1 = 2,147,483,647|  
|큐브의 동작|2^31-1 = 2,147,483,647|  
|큐브의 파티션|2^31-1 = 2,147,483,647|  
|큐브의 번역|2^31-1 = 2,147,483,647|  
|파티션의 집계|2^31-1 = 2,147,483,647|  
|쿼리에서 반환된 셀|2^31-1 = 2,147,483,647|  
|원본 쿼리의 레코드 크기|64K|  
|개체 이름의 길이|100 문자|  
|데이터 마이닝 모델 특성 열의 고유한 최대 상태 수|2^31-1 = 2,147,483,647|  
|고려되는 최대 특성 수(기능 선택)|2^31-1 = 2,147,483,647|  
  
 개체 이름 지정 지침에 대 한 자세한 내용은 개체 [및 개체 특징](../scripting-language-assl/assl-objects-and-object-characteristics.md)을 참조 하십시오.  
  
 OLAP (온라인 분석 처리) 및 데이터 마이닝의 데이터 원본 제한 사항에 대 한 자세한 내용은 [지원 되는 데이터 원본 &#40;Ssas 다차원&#41;](../supported-data-sources-ssas-multidimensional.md), [지원 되는 데이터 원본 &#40;ssas 다차원&#41;](../supported-data-sources-ssas-multidimensional.md)및 [개체 특징](../scripting-language-assl/assl-objects-and-object-characteristics.md)을 참조 하십시오.  
  
##  <a name="sharepoint-deploymentmode1"></a><a name="bkmk_sharepoint"></a>SharePoint (DeploymentMode = 1)  
  
|Object|최대 크기/개수|  
|------------|----------------------------|  
|인스턴스의 데이터베이스|2^31-1 = 2,147,483,647|  
|데이터베이스의 테이블|2^31-1 = 2,147,483,647|  
|테이블의 열|2 ^ 31-1 = 2147483647 **경고:** 테이블의 총 열 개수는 같은 테이블에 연결 된 측정값 및 계산 된 열의 총 수에 따라 달라 집니다. 테이블의 '열 + 측정값 + 계산 열' 개수의 최대값은 2^31-1 = 2,147,483,647입니다.|  
|테이블의 행|무제한 **경고:** 단일 열에 1999999997 개 이상의 고유 값이 포함 될 수 없는 제한이 있습니다.|  
|테이블의 계층|2^31-1 = 2,147,483,647|  
|계층의 수준|2^31-1 = 2,147,483,647|  
|관계|2^31-1 = 2,147,483,647|  
|테이블의 키 열|2^31-1 = 2,147,483,647|  
|테이블의 측정값|2 ^ 31-1 = 2147483647 **경고:** 테이블의 총 측정값 수는 동일한 테이블에 연결 된 열과 계산 된 열의 총 수에 따라 달라 집니다. 테이블의 '열 + 측정값 + 계산 열' 개수의 최대값은 2^31-1 = 2,147,483,647입니다.|  
|테이블의 계산 열|2 ^ 31-1 = 2147483647 **경고:** 테이블의 총 계산 열 수는 동일한 테이블에 연결 된 총 열 및 측정값 수에 따라 달라 집니다. 테이블의 '열 + 측정값 + 계산 열' 개수의 최대값은 2^31-1 = 2,147,483,647입니다.|  
|쿼리에서 반환된 셀|2^31-1 = 2,147,483,647|  
|원본 쿼리의 레코드 크기|64K|  
|개체 이름의 길이|100 문자|  
  
##  <a name="tabular-deploymentmode2"></a><a name="bkmk_vertipaq"></a>테이블 형식 (DeploymentMode = 2)  
  
|Object|최대 크기/개수|  
|------------|----------------------------|  
|인스턴스의 데이터베이스|2^31-1 = 2,147,483,647|  
|데이터베이스의 테이블|2^31-1 = 2,147,483,647|  
|테이블의 열|2 ^ 31-1 = 2147483647 **경고:** 테이블의 총 열 개수는 같은 테이블에 연결 된 측정값 및 계산 된 열의 총 수에 따라 달라 집니다. 테이블의 '열 + 측정값 + 계산 열' 개수의 최대값은 2^31-1 = 2,147,483,647입니다.|  
|테이블의 행|무제한 **경고:** 테이블의 단일 열에 1999999997 개 이상의 고유 값이 포함 될 수 없도록 제한 됩니다.|  
|테이블의 계층|2^31-1 = 2,147,483,647|  
|계층의 수준|2^31-1 = 2,147,483,647|  
|관계|2^31-1 = 2,147,483,647|  
|테이블의 키 열|2^31-1 = 2,147,483,647|  
|테이블의 측정값|2 ^ 31-1 = 2147483647 **경고:** 테이블의 총 측정값 수는 동일한 테이블에 연결 된 열과 계산 된 열의 총 수에 따라 달라 집니다. 테이블의 '열 + 측정값 + 계산 열' 개수의 최대값은 2^31-1 = 2,147,483,647입니다.|  
|테이블의 계산 열|2 ^ 31-1 = 2147483647 **경고:** 테이블의 총 계산 열 수는 동일한 테이블에 연결 된 총 열 및 측정값 수에 따라 달라 집니다. 테이블의 '열 + 측정값 + 계산 열' 개수의 최대값은 2^31-1 = 2,147,483,647입니다.|  
|쿼리에서 반환된 셀|2^31-1 = 2,147,483,647|  
|원본 쿼리의 레코드 크기|64K|  
|개체 이름의 길이|100 문자|  
  
## <a name="see-also"></a>참고 항목  
 [Analysis Services 인스턴스의 서버 모드 확인](../../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [일반 속성](../../server-properties/general-properties.md)  
  
  