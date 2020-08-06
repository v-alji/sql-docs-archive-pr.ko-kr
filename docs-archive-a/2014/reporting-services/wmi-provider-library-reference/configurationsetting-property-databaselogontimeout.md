---
title: DatabaseLogonTimeout 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonTimeout property
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4920f5ef2282478f4d12a19b0806cf6ff9632cac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737666"
---
# <a name="databaselogontimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d79f9-102">DatabaseLogonTimeout 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d79f9-102">DatabaseLogonTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d79f9-103">보고서 서버 데이터베이스에 대한 로그온 시도가 실패할 때까지 기다리는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d79f9-103">Specifies the number of seconds to wait before an attempt to log on to the report server database fails.</span></span> <span data-ttu-id="d79f9-104">**0** 값은 무한 대기 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d79f9-104">A value of **0** indicates an infinite wait time.</span></span> <span data-ttu-id="d79f9-105">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="d79f9-105">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d79f9-106">구문</span><span class="sxs-lookup"><span data-stu-id="d79f9-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="d79f9-107">속성 값</span><span class="sxs-lookup"><span data-stu-id="d79f9-107">Property Values</span></span>  
 <span data-ttu-id="d79f9-108">시간(초)을 나타내는 부호 있는 32비트 정수 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d79f9-108">A 32-bit signed integer object that represents the number of seconds.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="d79f9-109">코드 예</span><span class="sxs-lookup"><span data-stu-id="d79f9-109">Example Code</span></span>  
 [<span data-ttu-id="d79f9-110">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="d79f9-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="d79f9-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d79f9-111">Requirements</span></span>  
 <span data-ttu-id="d79f9-112">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d79f9-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d79f9-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d79f9-113">See Also</span></span>  
 [<span data-ttu-id="d79f9-114">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="d79f9-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
