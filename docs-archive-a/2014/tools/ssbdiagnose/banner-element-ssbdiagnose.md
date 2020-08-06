---
title: 배너 요소 (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13238ac4ef1745dea4fbf3392484ac6137c09df1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742724"
---
# <a name="banner-element-ssbdiagnose"></a>Banner 요소(ssbdiagnose)
  **ssbdiagnose** 출력 XML 파일을 생성한 유틸리티를 식별합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>요소 특성  
  
|attribute|Description|  
|---------------|-----------------|  
|`title`|**ssbdiagnose** XML 출력 파일을 생성한 유틸리티를 식별합니다.|  
|`product`|**ssbdiagnose** XML 출력 파일을 생성한 제품을 식별합니다.|  
|`version`|XML 출력 파일을 생성한 유틸리티의 버전을 식별합니다.|  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특성|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|**ssbdiagnose** 출력 XML 파일당 한 번|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[DiagnosticInformation 요소&#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**자식 요소**|없음|  
  
## <a name="example"></a>예제  
 다음은 Banner 요소의 예입니다.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>참고 항목  
 [ssbdiagnose 유틸리티&#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
