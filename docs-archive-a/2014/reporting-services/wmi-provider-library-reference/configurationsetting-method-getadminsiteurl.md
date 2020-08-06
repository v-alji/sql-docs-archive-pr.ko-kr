---
title: GetAdminSiteUrl 메서드(WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cae1a6f7e363ddce8c47c00eb5ef25fc832e59c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649911"
---
# <a name="getadminsiteurl-method-wmi"></a><span data-ttu-id="0a156-102">GetAdminSiteUrl 메서드(WMI)</span><span class="sxs-lookup"><span data-stu-id="0a156-102">GetAdminSiteUrl Method (WMI)</span></span>
  <span data-ttu-id="0a156-103">보고서 서버가 통합되어 있는 Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]또는 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 팜에 대한 중앙 관리 웹 사이트의 절대 URL을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0a156-103">Gets the absolute URL for the Central Administration Web site for the Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] farm that the report server is integrated with.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a156-104">구문</span><span class="sxs-lookup"><span data-stu-id="0a156-104">Syntax</span></span>  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a156-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a156-105">Parameters</span></span>  
 <span data-ttu-id="0a156-106">*AdminSiteUrl*</span><span class="sxs-lookup"><span data-stu-id="0a156-106">*AdminSiteUrl*</span></span>  
 <span data-ttu-id="0a156-107">[out] 보고서 서버가 통합되어 있는 SharePoint 팜에 대한 중앙 관리 웹 사이트의 절대 URL이 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="0a156-107">[out] A string that contains the absolute URL for the Central Administration Web site for the SharePoint farm that the report server is integrated with.</span></span>  
  
 <span data-ttu-id="0a156-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="0a156-108">*HRESULT*</span></span>  
 <span data-ttu-id="0a156-109">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0a156-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a156-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="0a156-110">Return Value</span></span>  
 <span data-ttu-id="0a156-111">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a156-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="0a156-112">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a156-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="0a156-113">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a156-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a156-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0a156-114">Requirements</span></span>  
 <span data-ttu-id="0a156-115">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a156-115">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a156-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a156-116">See Also</span></span>  
 [<span data-ttu-id="0a156-117">MSReportServer_ConfigurationSetting 메서드</span><span class="sxs-lookup"><span data-stu-id="0a156-117">MSReportServer_ConfigurationSetting Methods</span></span>](msreportserver-configurationsetting-methods.md)  
  
  
