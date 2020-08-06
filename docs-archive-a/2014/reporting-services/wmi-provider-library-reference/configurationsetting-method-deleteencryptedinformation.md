---
title: DeleteEncryptedInformation 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d00dc3e90816cd04c84f124cdc3d25a9ac122bba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649924"
---
# <a name="deleteencryptedinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="13d6c-102">DeleteEncryptedInformation 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="13d6c-102">DeleteEncryptedInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="13d6c-103">보고서 서버 데이터베이스에서 암호화된 정보를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-103">Deletes the encrypted information from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d6c-104">구문</span><span class="sxs-lookup"><span data-stu-id="13d6c-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13d6c-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="13d6c-105">Parameters</span></span>  
 <span data-ttu-id="13d6c-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="13d6c-106">*HRESULT*</span></span>  
 <span data-ttu-id="13d6c-107">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="13d6c-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="13d6c-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="13d6c-109">[out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13d6c-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="13d6c-110">Return Value</span></span>  
 <span data-ttu-id="13d6c-111">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="13d6c-112">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="13d6c-113">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13d6c-114">설명</span><span class="sxs-lookup"><span data-stu-id="13d6c-114">Remarks</span></span>  
 <span data-ttu-id="13d6c-115">이 메서드를 호출하면 다음 데이터가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-115">When this method is invoked, the following data is deleted:</span></span>  
  
-   <span data-ttu-id="13d6c-116">사용자 이름 및 암호를 비롯하여 암호화되는 데이터 원본 정보</span><span class="sxs-lookup"><span data-stu-id="13d6c-116">Data source information that is encrypted, including user name and password.</span></span>  
  
-   <span data-ttu-id="13d6c-117">배달 확장 프로그램 인터페이스를 사용하여 암호화되는 구독 데이터</span><span class="sxs-lookup"><span data-stu-id="13d6c-117">Subscription data that is encrypted using the delivery extension interfaces.</span></span>  
  
-   <span data-ttu-id="13d6c-118">보고서 서버 데이터베이스에 있는 키 테이블의 모든 정보</span><span class="sxs-lookup"><span data-stu-id="13d6c-118">All the information from the keys table in the report server database.</span></span>  
  
 <span data-ttu-id="13d6c-119">이 메서드를 호출한 후 사용자는 보고서 서버 데이터베이스를 사용하는 각 컴퓨터를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-119">After this method is invoked, the user must initialize each computer that uses the report server database.</span></span>  
  
 <span data-ttu-id="13d6c-120">DeleteEncryptedInformation 메서드를 호출해도 보고서 서버 구성 파일에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13d6c-120">Calling the DeleteEncryptedInformation method does not affect the report server configuration file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d6c-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="13d6c-121">Requirements</span></span>  
 <span data-ttu-id="13d6c-122">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13d6c-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d6c-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13d6c-123">See Also</span></span>  
 [<span data-ttu-id="13d6c-124">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="13d6c-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
