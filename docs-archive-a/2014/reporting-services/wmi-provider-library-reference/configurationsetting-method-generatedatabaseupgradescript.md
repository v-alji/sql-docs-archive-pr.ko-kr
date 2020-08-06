---
title: GenerateDatabaseUpgradeScript 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseUpgradeScript method
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6a619584b9f1cc095f8f624670386d388426e4a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649912"
---
# <a name="generatedatabaseupgradescript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7de73-102">GenerateDatabaseUpgradeScript 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7de73-102">GenerateDatabaseUpgradeScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7de73-103">보고서 서버 데이터베이스를 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 스키마로 업그레이드하는 데 사용할 수 있는 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-103">Generates a script that can be used to upgrade the report server database to the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] schema.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7de73-104">구문</span><span class="sxs-lookup"><span data-stu-id="7de73-104">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7de73-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7de73-105">Parameters</span></span>  
 <span data-ttu-id="7de73-106">*Databasename*</span><span class="sxs-lookup"><span data-stu-id="7de73-106">*Databasename*</span></span>  
 <span data-ttu-id="7de73-107">업그레이드할 보고서 서버 데이터베이스의 이름이 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-107">A string containing the name of the report server database to upgrade.</span></span>  
  
 <span data-ttu-id="7de73-108">*ServerVersion*</span><span class="sxs-lookup"><span data-stu-id="7de73-108">*ServerVersion*</span></span>  
 <span data-ttu-id="7de73-109">보고서 서버의 버전이 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-109">A string containing the version of the report server.</span></span>  
  
 <span data-ttu-id="7de73-110">*스크립트*</span><span class="sxs-lookup"><span data-stu-id="7de73-110">*Script*</span></span>  
 <span data-ttu-id="7de73-111">[out] 생성된 SQL 스크립트가 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-111">[out] A string containing the generated SQL script.</span></span>  
  
 <span data-ttu-id="7de73-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="7de73-112">*HRESULT*</span></span>  
 <span data-ttu-id="7de73-113">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7de73-114">Return Value</span><span class="sxs-lookup"><span data-stu-id="7de73-114">Return Value</span></span>  
 <span data-ttu-id="7de73-115">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-115">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="7de73-116">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-116">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="7de73-117">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-117">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7de73-118">설명</span><span class="sxs-lookup"><span data-stu-id="7de73-118">Remarks</span></span>  
 <span data-ttu-id="7de73-119">생성된 스크립트는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]및 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7de73-119">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7de73-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7de73-120">Requirements</span></span>  
 <span data-ttu-id="7de73-121">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7de73-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de73-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7de73-122">See Also</span></span>  
 [<span data-ttu-id="7de73-123">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="7de73-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
