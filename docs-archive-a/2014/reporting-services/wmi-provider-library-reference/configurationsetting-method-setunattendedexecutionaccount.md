---
title: SetUnattendedExecutionAccount 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73cf4c633c51de1e3e6b878c66d73ee710e98df6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737708"
---
# <a name="setunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ea442-102">SetUnattendedExecutionAccount 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ea442-102">SetUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ea442-103">무인 모드로 보고서를 실행하는 데 사용되는 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-103">Specifies the account used to execute reports unattended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea442-104">구문</span><span class="sxs-lookup"><span data-stu-id="ea442-104">Syntax</span></span>  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea442-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ea442-105">Parameters</span></span>  
 <span data-ttu-id="ea442-106">*UserName*</span><span class="sxs-lookup"><span data-stu-id="ea442-106">*UserName*</span></span>  
 <span data-ttu-id="ea442-107">무인 실행에 사용할 Windows 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-107">A Windows account to be used for unattended executions.</span></span>  
  
 <span data-ttu-id="ea442-108">*암호*</span><span class="sxs-lookup"><span data-stu-id="ea442-108">*Password*</span></span>  
 <span data-ttu-id="ea442-109">지정된 계정의 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-109">The password for the specified account.</span></span>  
  
 <span data-ttu-id="ea442-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="ea442-110">*HRESULT*</span></span>  
 <span data-ttu-id="ea442-111">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea442-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="ea442-112">Return Value</span></span>  
 <span data-ttu-id="ea442-113">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="ea442-114">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="ea442-115">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea442-116">설명</span><span class="sxs-lookup"><span data-stu-id="ea442-116">Remarks</span></span>  
 <span data-ttu-id="ea442-117">SetUnattendedExecutionAccount 메서드는 보고서 서버가 지정된 사용자로 로그인할 수 있는지 여부를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-117">The SetUnattendedExecutionAccount method does not verify whether the report server can log in as the specified user.</span></span>  
  
 <span data-ttu-id="ea442-118">보고서 서버의 Windows 서비스 컨텍스트에서 무인 실행을 실행하기 위해 SetUnattendedExecutionAccount 메서드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea442-118">It is not possible to use the SetUnattendedExecutionAccount method to run unattended executions in the context of the report server Windows service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea442-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ea442-119">Requirements</span></span>  
 <span data-ttu-id="ea442-120">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea442-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea442-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea442-121">See Also</span></span>  
 [<span data-ttu-id="ea442-122">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="ea442-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
