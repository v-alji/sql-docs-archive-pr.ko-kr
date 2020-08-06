---
title: DeleteEncryptionKey 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptionKey method
ms.assetid: ed2f25b6-6a63-468d-9279-a577ca01b096
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e302659615bd620b3b0ed802b83aafc4e9506d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649917"
---
# <a name="deleteencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="b8b04-102">DeleteEncryptionKey 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="b8b04-102">DeleteEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="b8b04-103">보고서 서버 데이터베이스에서 암호화 키를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-103">Deletes the encryption keys from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b04-104">구문</span><span class="sxs-lookup"><span data-stu-id="b8b04-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptionKeys(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptionKeys(string InstallationID, out Int32 HRESULT,   
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8b04-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b8b04-105">Parameters</span></span>  
 <span data-ttu-id="b8b04-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="b8b04-106">*InstallationID*</span></span>  
 <span data-ttu-id="b8b04-107">보고서 서버 데이터베이스의 키 테이블에 있는 보고서 서버의 설치 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-107">The installation ID of a report server that is in the keys table of the report server database.</span></span>  
  
 <span data-ttu-id="b8b04-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="b8b04-108">*HRESULT*</span></span>  
 <span data-ttu-id="b8b04-109">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="b8b04-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="b8b04-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="b8b04-111">[out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8b04-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="b8b04-112">Return Value</span></span>  
 <span data-ttu-id="b8b04-113">메서드 호출의 성공 또는 실패를 나타내는 HRESULT를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-113">Returns an HRESULT indicating success or failure of the method call.</span></span> <span data-ttu-id="b8b04-114">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="b8b04-115">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8b04-116">설명</span><span class="sxs-lookup"><span data-stu-id="b8b04-116">Remarks</span></span>  
 <span data-ttu-id="b8b04-117">*DeleteEncryptionKey* 메서드는 보고서 서버 데이터베이스의 보안 정보에 대한 액세스 권한이 있는 보고서 서버의 키 테이블에서 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-117">The *DeleteEncryptionKey* method deletes entries from the keys table for any report servers that have access to the secure information in the report server database.</span></span> <span data-ttu-id="b8b04-118">지정된 *InstallationID* 매개 변수가 데이터베이스의 설치 ID와 일치하지 않으면 메서드에서 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8b04-118">If the *InstallationID* parameter specified does not correspond to an installation ID in the database, the method returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8b04-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b8b04-119">Requirements</span></span>  
 <span data-ttu-id="b8b04-120">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8b04-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b04-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8b04-121">See Also</span></span>  
 [<span data-ttu-id="b8b04-122">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="b8b04-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
