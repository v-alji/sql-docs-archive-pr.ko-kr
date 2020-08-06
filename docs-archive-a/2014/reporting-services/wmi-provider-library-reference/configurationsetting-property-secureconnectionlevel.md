---
title: SecureConnectionLevel 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SecureConnectionLevel
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1b3bccc8a7fee3899fa21208d83a718a33f5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737630"
---
# <a name="secureconnectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7f9d2-102">SecureConnectionLevel 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7f9d2-102">SecureConnectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7f9d2-103">RSReportServer.config 파일에 지정된 보안 연결 수준을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7f9d2-103">Returns the secure connection level specified in the RSReportServer.config file.</span></span> <span data-ttu-id="7f9d2-104">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="7f9d2-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9d2-105">구문</span><span class="sxs-lookup"><span data-stu-id="7f9d2-105">Syntax</span></span>  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a><span data-ttu-id="7f9d2-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="7f9d2-106">Property Values</span></span>  
 <span data-ttu-id="7f9d2-107">보안 연결 수준을 나타내는 `Integer` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7f9d2-107">An `Integer` value that represents the secure connection level.</span></span> <span data-ttu-id="7f9d2-108">반환 값은 SSL이 구성되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f9d2-108">The return values indicate that the SSL is either configured or not.</span></span> <span data-ttu-id="7f9d2-109">값이 1보다 크거나 같으면 SSL이 설정되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f9d2-109">A value of greater than or equal to 1 indicates that SSL is turned on.</span></span> <span data-ttu-id="7f9d2-110">값이 0이면 SSL이 해제되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7f9d2-110">A value of 0 indicates that SSL is turned off.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="7f9d2-111">코드 예</span><span class="sxs-lookup"><span data-stu-id="7f9d2-111">Example Code</span></span>  
 [<span data-ttu-id="7f9d2-112">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="7f9d2-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="7f9d2-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7f9d2-113">Requirements</span></span>  
 <span data-ttu-id="7f9d2-114">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f9d2-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9d2-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7f9d2-115">See Also</span></span>  
 [<span data-ttu-id="7f9d2-116">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="7f9d2-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
