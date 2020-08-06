---
title: rsInternalError - Reporting Services 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 85b88519df810f60c580ad2d6eb355dde236d081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651456"
---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Reporting Services 오류
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|rsInternalError|  
|이벤트 원본|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|구성 요소|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|메시지 텍스트|보고서 서버에서 내부 오류가 발생했습니다. 자세한 내용은 오류 로그를 참고하세요.|  
  
## <a name="explanation"></a>설명  
 이 메시지는 일반 오류 메시지이며 세부 정보를 제공하는 보다 자세한 오류가 제공되는 경우도 있습니다.  
  
 내부 오류는 일반적인 오류가 아닙니다. 따라서 이 오류가 발생할 경우 보고서 서버 추적 로그에서 자세한 내용을 볼 수 있습니다. 또한 오류가 발생한 동일한 컴퓨터에서 로컬 관리자로 실행 중인 경우 호출 스택에서 자세한 내용을 볼 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
 이 메시지의 특정 원인을 확인 하려면 \Microsoft SQL Server\MSRS12. \<instancename > 에 있는 보고서 서버 로그 파일을 검토 합니다. \Reporting Services\logfiles 자세한 내용은 [Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md)를 참조하세요.  
  
 호출 스택을 보려면 오류가 발생한 페이지를 마우스 오른쪽 단추로 클릭한 다음 **원본 보기**를 가리킵니다. 호출 스택을 보려면 오류가 발생한 컴퓨터에서 관리자 권한이 필요합니다.  
  
 추가로 제공되는 정보가 없는 경우 요청을 다시 시도할 수 있습니다.  
  
## <a name="internal-only"></a>내부 전용  
  
## <a name="see-also"></a>참고 항목  
 [보고서 서버 서비스 시작 및 중지](../report-server/start-and-stop-the-report-server-service.md)  
  
  
