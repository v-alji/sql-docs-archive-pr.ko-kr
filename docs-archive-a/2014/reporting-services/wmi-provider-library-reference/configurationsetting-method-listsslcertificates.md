---
title: ListSSLCertificates 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6a5ced8371817adc44bbbc89400dc83e0dfccef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649895"
---
# <a name="listsslcertificates-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7b087-102">ListSSLCertificates 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7b087-102">ListSSLCertificates Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7b087-103">보고서 서버 컴퓨터의 인증서 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-103">Returns a list of certificates on the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b087-104">구문</span><span class="sxs-lookup"><span data-stu-id="7b087-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b087-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7b087-105">Parameters</span></span>  
 <span data-ttu-id="7b087-106">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="7b087-106">*CertificateHash[]*</span></span>  
 <span data-ttu-id="7b087-107">[out] 인증서 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-107">[out] The certificate hashes.</span></span>  
  
 <span data-ttu-id="7b087-108">*CertName[]*</span><span class="sxs-lookup"><span data-stu-id="7b087-108">*CertName[]*</span></span>  
 <span data-ttu-id="7b087-109">[out] 인증서 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-109">[out] Names of the certificate.</span></span>  
  
 <span data-ttu-id="7b087-110">*HostName[]*</span><span class="sxs-lookup"><span data-stu-id="7b087-110">*HostName[]*</span></span>  
 <span data-ttu-id="7b087-111">[out] 인증서의 호스트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-111">[out] The host names for the certificates.</span></span>  
  
 <span data-ttu-id="7b087-112">*길이*</span><span class="sxs-lookup"><span data-stu-id="7b087-112">*Length*</span></span>  
 <span data-ttu-id="7b087-113">[out] *CertificateHash*, *CertName* 및 *HostName* 배열의 길이를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-113">[out] Represents the length of the *CertificateHash*, *CertName* and *HostName* arrays.</span></span>  
  
 <span data-ttu-id="7b087-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="7b087-114">*HRESULT*</span></span>  
 <span data-ttu-id="7b087-115">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b087-116">Return Value</span><span class="sxs-lookup"><span data-stu-id="7b087-116">Return Value</span></span>  
 <span data-ttu-id="7b087-117">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="7b087-118">0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b087-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b087-119">설명</span><span class="sxs-lookup"><span data-stu-id="7b087-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b087-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7b087-120">Requirements</span></span>  
 <span data-ttu-id="7b087-121">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b087-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b087-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b087-122">See Also</span></span>  
 [<span data-ttu-id="7b087-123">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="7b087-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
