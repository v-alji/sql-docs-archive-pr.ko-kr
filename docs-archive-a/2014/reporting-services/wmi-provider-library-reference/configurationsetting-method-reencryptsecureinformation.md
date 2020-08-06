---
title: ReencryptSecureInformation 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1a0c657b69d624df8895ae4d5a6d12277b011b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653197"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="f4c16-102">ReencryptSecureInformation 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="f4c16-102">ReencryptSecureInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="f4c16-103">새 암호화 키를 생성하고 이 새 키를 사용하여 카탈로그에 있는 모든 보안 정보를 다시 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-103">Generates a new encryption key and re-encrypts all secure information in the catalog using this new key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c16-104">구문</span><span class="sxs-lookup"><span data-stu-id="f4c16-104">Syntax</span></span>  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4c16-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f4c16-105">Parameters</span></span>  
 <span data-ttu-id="f4c16-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="f4c16-106">*HRESULT*</span></span>  
 <span data-ttu-id="f4c16-107">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="f4c16-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="f4c16-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="f4c16-109">[out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4c16-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="f4c16-110">Return Value</span></span>  
 <span data-ttu-id="f4c16-111">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="f4c16-112">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="f4c16-113">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4c16-114">설명</span><span class="sxs-lookup"><span data-stu-id="f4c16-114">Remarks</span></span>  
 <span data-ttu-id="f4c16-115">관리자는 ReencryptSecureInformation 메서드를 사용하여 기존 암호화 키를 새 키로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-115">The ReencryptSecureInformation method allows the administrator to replace the existing encryption key with a new key.</span></span>  
  
 <span data-ttu-id="f4c16-116">이 메서드가 호출되면 보고서 서버가 새 암호화 키를 생성하고 이 새 암호화 키로 모든 암호화 내용을 반복하여 다시 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-116">When this method is invoked, the report server generates a new encryption key and iterates through all encrypted content to re-encrypt it with the new encryption key.</span></span>  
  
 <span data-ttu-id="f4c16-117">배달 확장 프로그램은 배달 설정 구조의 보안 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-117">Delivery extensions can store secured information in their delivery settings structures.</span></span> <span data-ttu-id="f4c16-118">ReencryptSecureInformation이 호출되면 보고서 서버가 각 구독 및 해당 배달 확장 프로그램을 로드하여 연결된 설정에 저장된 정보를 다시 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-118">When ReencryptSecureInformation is called, the report server loads each subscription and the corresponding delivery extension to re-encrypt information stored in the associated settings.</span></span>  
  
 <span data-ttu-id="f4c16-119">이 메서드를 스케일 아웃 배포의 컴퓨터에서 실행하면 스케일 아웃 배포의 각 컴퓨터를 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4c16-119">If this method is run on a computer in a scale-out deployment, each computer in the scale-out deployment will need to be initialized again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4c16-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f4c16-120">Requirements</span></span>  
 <span data-ttu-id="f4c16-121">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c16-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c16-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4c16-122">See Also</span></span>  
 [<span data-ttu-id="f4c16-123">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="f4c16-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
