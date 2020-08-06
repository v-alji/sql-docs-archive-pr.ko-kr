---
title: RestoreEncryptionKey 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e67478541bab615a6d441ae273ed3385a8654203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737744"
---
# <a name="restoreencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="75fd6-102">RestoreEncryptionKey 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="75fd6-102">RestoreEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="75fd6-103">지정된 암호화 키를 보고서 서버 데이터베이스에 다시 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-103">Reapplies the specified encryption key to the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75fd6-104">구문</span><span class="sxs-lookup"><span data-stu-id="75fd6-104">Syntax</span></span>  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75fd6-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="75fd6-105">Parameters</span></span>  
 <span data-ttu-id="75fd6-106">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="75fd6-106">*KeyFile[]*</span></span>  
 <span data-ttu-id="75fd6-107">[out] 암호화된 암호화 키를 포함하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-107">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="75fd6-108">*길이*</span><span class="sxs-lookup"><span data-stu-id="75fd6-108">*Length*</span></span>  
 <span data-ttu-id="75fd6-109">[out] 메서드에서 반환된 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-109">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="75fd6-110">*암호*</span><span class="sxs-lookup"><span data-stu-id="75fd6-110">*Password*</span></span>  
 <span data-ttu-id="75fd6-111">암호화 키를 암호화하는 데 사용되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-111">A string used to encrypt the encryption key.</span></span>  
  
 <span data-ttu-id="75fd6-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="75fd6-112">*HRESULT*</span></span>  
 <span data-ttu-id="75fd6-113">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="75fd6-114">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="75fd6-114">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="75fd6-115">[out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-115">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75fd6-116">Return Value</span><span class="sxs-lookup"><span data-stu-id="75fd6-116">Return Value</span></span>  
 <span data-ttu-id="75fd6-117">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="75fd6-118">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="75fd6-119">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75fd6-120">설명</span><span class="sxs-lookup"><span data-stu-id="75fd6-120">Remarks</span></span>  
 <span data-ttu-id="75fd6-121">보고서 서버 데이터베이스에 보고서 서버에 대한 항목이 이미 있으면 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-121">If an entry already exists for the report server in the report server database, it is deleted.</span></span> <span data-ttu-id="75fd6-122">그런 다음, 지정된 암호화 키와 보고서 서버의 공개 키를 사용하여 새로운 항목이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-122">The new entry is then created using the specified encryption key and the report server's public key.</span></span>  
  
 <span data-ttu-id="75fd6-123">이 메서드는 암호화 키 목록을 지우는 [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) 메서드 다음에 호출하는 것이 가장 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="75fd6-123">The method is most effective when called after the [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) method, which clears the list of encryption keys.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75fd6-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="75fd6-124">Requirements</span></span>  
 <span data-ttu-id="75fd6-125">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75fd6-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fd6-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75fd6-126">See Also</span></span>  
 [<span data-ttu-id="75fd6-127">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="75fd6-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
