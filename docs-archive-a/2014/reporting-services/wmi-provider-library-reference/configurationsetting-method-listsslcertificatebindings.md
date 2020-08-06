---
title: ListSSLCertificateBindings 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56b19a138dc95b94a20183909dd444c90b158b26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649898"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="4a5bb-102">ListSSLCertificateBindings 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="4a5bb-102">ListSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="4a5bb-103">컴퓨터에 설치된 SSL 인증서 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-103">Returns a list of installed SSL certificates on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5bb-104">구문</span><span class="sxs-lookup"><span data-stu-id="4a5bb-104">Syntax</span></span>  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a5bb-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4a5bb-105">Parameters</span></span>  
 <span data-ttu-id="4a5bb-106">*LCID*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-106">*LCID*</span></span>  
 <span data-ttu-id="4a5bb-107">반환되는 오류 메시지에 사용할 로캘입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-107">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="4a5bb-108">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-108">*Application[]*</span></span>  
 <span data-ttu-id="4a5bb-109">[out] 인증서 바인딩이 있는 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-109">[out] The applications that have certificate bindings.</span></span>  
  
 <span data-ttu-id="4a5bb-110">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-110">*CertificateHash[]*</span></span>  
 <span data-ttu-id="4a5bb-111">[out] 인증서에 대한 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-111">[out] The hashes for the certificates.</span></span>  
  
 <span data-ttu-id="4a5bb-112">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-112">*IPAddress[]*</span></span>  
 <span data-ttu-id="4a5bb-113">[out] 애플리케이션의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-113">[out] The IP address for the applications.</span></span>  
  
 <span data-ttu-id="4a5bb-114">*Port[]*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-114">*Port[]*</span></span>  
 <span data-ttu-id="4a5bb-115">[out] rsreportserver.config의 바인딩에 저장되는 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-115">[out] The port number stored in the binding in rsreportserver.config.</span></span>  
  
 <span data-ttu-id="4a5bb-116">*Errors[]*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-116">*Errors[]*</span></span>  
 <span data-ttu-id="4a5bb-117">[out] 발생한 오류에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-117">[out] The descriptions for errors that occurred.</span></span>  
  
 <span data-ttu-id="4a5bb-118">*길이*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-118">*Length*</span></span>  
 <span data-ttu-id="4a5bb-119">[out] 메서드에서 반환된 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-119">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="4a5bb-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="4a5bb-120">*HRESULT*</span></span>  
 <span data-ttu-id="4a5bb-121">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a5bb-122">Return Value</span><span class="sxs-lookup"><span data-stu-id="4a5bb-122">Return Value</span></span>  
 <span data-ttu-id="4a5bb-123">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="4a5bb-124">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="4a5bb-125">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4a5bb-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a5bb-126">설명</span><span class="sxs-lookup"><span data-stu-id="4a5bb-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a5bb-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4a5bb-127">Requirements</span></span>  
 <span data-ttu-id="4a5bb-128">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a5bb-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5bb-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a5bb-129">See Also</span></span>  
 [<span data-ttu-id="4a5bb-130">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="4a5bb-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
