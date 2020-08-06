---
title: RemoveSSLCertificateBindings 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveSSLCertificateBindings method
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d42d17d9c92f2e100a7800e607536ff6c7eab891
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735935"
---
# <a name="removesslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d200a-102">RemoveSSLCertificateBindings 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d200a-102">RemoveSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d200a-103">SSL 인증서 바인딩을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-103">Removes an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d200a-104">구문</span><span class="sxs-lookup"><span data-stu-id="d200a-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveSSLCertificateBindings(string Application,  
    string CertificateHash, string IPAddress, Int32 Port, Int32 Lcid,  
    out string Error, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d200a-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d200a-105">Parameters</span></span>  
 <span data-ttu-id="d200a-106">*애플리케이션*</span><span class="sxs-lookup"><span data-stu-id="d200a-106">*Application*</span></span>  
 <span data-ttu-id="d200a-107">인증서 바인딩을 제거해야 하는 애플리케이션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-107">The name of application for which the certificate binding should be removed.</span></span>  
  
 <span data-ttu-id="d200a-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="d200a-108">*CertificateHash*</span></span>  
 <span data-ttu-id="d200a-109">인증서에 대한 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="d200a-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="d200a-110">*IPAddress*</span></span>  
 <span data-ttu-id="d200a-111">애플리케이션의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="d200a-112">*포트*</span><span class="sxs-lookup"><span data-stu-id="d200a-112">*Port*</span></span>  
 <span data-ttu-id="d200a-113">바인딩과 연결된 SSL 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="d200a-114">*lcid*</span><span class="sxs-lookup"><span data-stu-id="d200a-114">*lcid*</span></span>  
 <span data-ttu-id="d200a-115">반환되는 오류 메시지에 사용할 로캘입니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-115">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="d200a-116">*오류*</span><span class="sxs-lookup"><span data-stu-id="d200a-116">*Error*</span></span>  
 <span data-ttu-id="d200a-117">[out] 발생한 오류에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-117">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="d200a-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d200a-118">*HRESULT*</span></span>  
 <span data-ttu-id="d200a-119">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d200a-120">Return Value</span><span class="sxs-lookup"><span data-stu-id="d200a-120">Return Value</span></span>  
 <span data-ttu-id="d200a-121">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d200a-122">0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d200a-123">설명</span><span class="sxs-lookup"><span data-stu-id="d200a-123">Remarks</span></span>  
 <span data-ttu-id="d200a-124">이 메서드는 rsreportserver.config 파일에서 특정 바인딩을 제거하고 HTTP.SYS 파일에서 특정 바인딩을 선택적으로 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d200a-124">This method removes the specific binding from the rsreportserver.config file and optionally HTTP.SYS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d200a-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d200a-125">Requirements</span></span>  
 <span data-ttu-id="d200a-126">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d200a-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d200a-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d200a-127">See Also</span></span>  
 [<span data-ttu-id="d200a-128">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="d200a-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
