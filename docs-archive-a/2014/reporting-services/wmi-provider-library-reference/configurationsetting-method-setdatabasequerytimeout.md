---
title: SetDatabaseQueryTimeout 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseQueryTimeout method
ms.assetid: bd2809e5-7848-45b3-a502-b04fc698b646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ab6b5bf27eca5e9d6d083d03af48c0ab71b4dd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737725"
---
# <a name="setdatabasequerytimeout-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="16724-102">SetDatabaseQueryTimeout 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="16724-102">SetDatabaseQueryTimeout Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="16724-103">보고서 서버 데이터베이스 쿼리에 대한 기본 제한 시간 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="16724-103">Specifies the default time-out value for report server database queries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16724-104">구문</span><span class="sxs-lookup"><span data-stu-id="16724-104">Syntax</span></span>  
  
```vb  
Public Sub SetDatabaseQueryTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseQueryTimeout (Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16724-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="16724-105">Parameters</span></span>  
 <span data-ttu-id="16724-106">*LogonTimeout*</span><span class="sxs-lookup"><span data-stu-id="16724-106">*LogonTimeout*</span></span>  
 <span data-ttu-id="16724-107">보고서 서버 데이터베이스 쿼리에 대한 기본 제한 시간 값(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="16724-107">The default timeout value, in seconds, for report server database queries.</span></span>  
  
 <span data-ttu-id="16724-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="16724-108">*HRESULT*</span></span>  
 <span data-ttu-id="16724-109">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="16724-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16724-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="16724-110">Return Value</span></span>  
 <span data-ttu-id="16724-111">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="16724-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="16724-112">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="16724-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="16724-113">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="16724-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16724-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="16724-114">Requirements</span></span>  
 <span data-ttu-id="16724-115">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16724-115">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16724-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="16724-116">See Also</span></span>  
 [<span data-ttu-id="16724-117">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="16724-117">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
