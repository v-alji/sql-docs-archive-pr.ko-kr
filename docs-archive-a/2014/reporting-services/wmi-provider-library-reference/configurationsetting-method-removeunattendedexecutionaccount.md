---
title: RemoveUnattendedExecutionAccount 메서드 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RemoveUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveUnattendedExecutionAccount method
ms.assetid: 77e371c1-7c26-44f9-9119-7c8dc838db32
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efe0523c9aa13315399c043367ef05a63da46e91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734919"
---
# <a name="removeunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="85585-102">RemoveUnattendedExecutionAccount 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="85585-102">RemoveUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="85585-103">보고서 서버 구성 파일에서 무인 실행 계정 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="85585-103">Deletes the unattended execution account entry from the report server configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85585-104">구문</span><span class="sxs-lookup"><span data-stu-id="85585-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveUnattendedExecutionAccount(ByRef HRESULT as Int32)  
```  
  
```csharp  
public void RemoveUnattendedExecutionAccount (out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85585-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="85585-105">Parameters</span></span>  
 <span data-ttu-id="85585-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="85585-106">*HRESULT*</span></span>  
 <span data-ttu-id="85585-107">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="85585-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85585-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="85585-108">Return Value</span></span>  
 <span data-ttu-id="85585-109">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85585-109">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="85585-110">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85585-110">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="85585-111">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85585-111">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85585-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="85585-112">Requirements</span></span>  
 <span data-ttu-id="85585-113">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85585-113">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85585-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85585-114">See Also</span></span>  
 [<span data-ttu-id="85585-115">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="85585-115">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
