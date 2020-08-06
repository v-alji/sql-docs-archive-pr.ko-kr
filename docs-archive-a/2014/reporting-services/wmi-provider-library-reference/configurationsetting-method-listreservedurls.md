---
title: ListReservedURLs 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7639741adb0c756961c4c6b63a3bffb627c4a89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649904"
---
# <a name="listreservedurls-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="651c8-102">ListReservedURLs 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="651c8-102">ListReservedURLs Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="651c8-103">보고서 서버의 모든 애플리케이션용으로 예약된 URL을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-103">Lists URLs reserved for all applications on the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="651c8-104">구문</span><span class="sxs-lookup"><span data-stu-id="651c8-104">Syntax</span></span>  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="651c8-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="651c8-105">Parameters</span></span>  
 <span data-ttu-id="651c8-106">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="651c8-106">*Application[]*</span></span>  
 <span data-ttu-id="651c8-107">[out] URL 예약이 있는 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-107">[out] The applications that have URL reservations.</span></span>  
  
 <span data-ttu-id="651c8-108">*UrlString[]*</span><span class="sxs-lookup"><span data-stu-id="651c8-108">*UrlString[]*</span></span>  
 <span data-ttu-id="651c8-109">[out] 예약된 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-109">[out] The URLs that are reserved.</span></span>  
  
 <span data-ttu-id="651c8-110">*Account[]*</span><span class="sxs-lookup"><span data-stu-id="651c8-110">*Account[]*</span></span>  
 <span data-ttu-id="651c8-111">[out] URL 예약에 대한 계정에 연결된 계정 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-111">[out] The account names associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="651c8-112">*AccountSID[]*</span><span class="sxs-lookup"><span data-stu-id="651c8-112">*AccountSID[]*</span></span>  
 <span data-ttu-id="651c8-113">[out] URL 예약에 대한 계정에 연결된 계정 SID입니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-113">[out] The account SIDs associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="651c8-114">*길이*</span><span class="sxs-lookup"><span data-stu-id="651c8-114">*Length*</span></span>  
 <span data-ttu-id="651c8-115">[out] 메서드에서 반환된 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-115">[out] The length of the arrays returned by the method.</span></span>  
  
 <span data-ttu-id="651c8-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="651c8-116">*HRESULT*</span></span>  
 <span data-ttu-id="651c8-117">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="651c8-118">Return Value</span><span class="sxs-lookup"><span data-stu-id="651c8-118">Return Value</span></span>  
 <span data-ttu-id="651c8-119">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="651c8-120">0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="651c8-120">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="651c8-121">설명</span><span class="sxs-lookup"><span data-stu-id="651c8-121">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="651c8-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="651c8-122">Requirements</span></span>  
 <span data-ttu-id="651c8-123">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="651c8-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="651c8-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="651c8-124">See Also</span></span>  
 [<span data-ttu-id="651c8-125">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="651c8-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
