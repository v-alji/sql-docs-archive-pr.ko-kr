---
title: CreateSSLCertificateBinding 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b9a5f9394d655f7b0592ea688a46f3ac2b9c153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649926"
---
# <a name="createsslcertificatebinding-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="de964-102">CreateSSLCertificateBinding 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="de964-102">CreateSSLCertificateBinding Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="de964-103">SSL 인증서 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="de964-103">Creates an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de964-104">구문</span><span class="sxs-lookup"><span data-stu-id="de964-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de964-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="de964-105">Parameters</span></span>  
 <span data-ttu-id="de964-106">*애플리케이션*</span><span class="sxs-lookup"><span data-stu-id="de964-106">*Application*</span></span>  
 <span data-ttu-id="de964-107">인증서 바인딩을 만들어야 하는 애플리케이션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="de964-107">The name of application that the certificate binding should be created for.</span></span>  
  
 <span data-ttu-id="de964-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="de964-108">*CertificateHash*</span></span>  
 <span data-ttu-id="de964-109">인증서에 대한 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="de964-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="de964-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="de964-110">*IPAddress*</span></span>  
 <span data-ttu-id="de964-111">애플리케이션의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="de964-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="de964-112">*포트*</span><span class="sxs-lookup"><span data-stu-id="de964-112">*Port*</span></span>  
 <span data-ttu-id="de964-113">바인딩과 연결된 SSL 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="de964-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="de964-114">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="de964-114">*Lcid*</span></span>  
 <span data-ttu-id="de964-115">반환되는 오류 메시지에 사용할 로캘입니다.</span><span class="sxs-lookup"><span data-stu-id="de964-115">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="de964-116">*오류*</span><span class="sxs-lookup"><span data-stu-id="de964-116">*Error*</span></span>  
 <span data-ttu-id="de964-117">[out] 발생한 오류에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="de964-117">[out] The description of the errors that occurred.</span></span>  
  
 <span data-ttu-id="de964-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="de964-118">*HRESULT*</span></span>  
 <span data-ttu-id="de964-119">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="de964-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de964-120">Return Value</span><span class="sxs-lookup"><span data-stu-id="de964-120">Return Value</span></span>  
 <span data-ttu-id="de964-121">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de964-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="de964-122">0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de964-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de964-123">설명</span><span class="sxs-lookup"><span data-stu-id="de964-123">Remarks</span></span>  
 <span data-ttu-id="de964-124">이 메서드는 애플리케이션의 rsreportserver.config에 바인딩을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="de964-124">This method adds a binding to rsreportserver.config for the application.</span></span> <span data-ttu-id="de964-125">HTTP.SYS에 바인딩이 없으면 이 파일에 바인딩이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="de964-125">If a binding does not already exist in HTTP.SYS, it is created there.</span></span>  
  
 <span data-ttu-id="de964-126">바인딩을 만들기 전에 메서드 호출은 지정된 애플리케이션에 대한 URL 예약을 검사하여 SSL 인증서 바인딩이 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="de964-126">Before creating the binding, the method call examines the Url Reservations for the specified application to determine if the SSL Certificate Binding is valid.</span></span>  
  
 <span data-ttu-id="de964-127">다음과 같은 경우 유효성 검사 후 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de964-127">The following conditions are validated and can result in errors:</span></span>  
  
1.  <span data-ttu-id="de964-128">인증서가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="de964-128">Certificate does not exist.</span></span>  
  
2.  <span data-ttu-id="de964-129">지정한 IPAddress가 이 컴퓨터의 IPAddress와 일치하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="de964-129">The IPAddress specified does not correspond to an IPAddress of this computer.</span></span>  
  
3.  <span data-ttu-id="de964-130">지정한 IPAddress가 DHCP IPAddress(정기적으로 변경됨)인 경우 대신 와일드카드 IP 주소(0.0.0.0)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="de964-130">The IPAddress specified is a DHCP IPAddress (changes periodically) - use the Wildcard IP address instead (0.0.0.0).</span></span>  
  
4.  <span data-ttu-id="de964-131">지정한 IPAddress가 URL 예약의 IP 주소와 일치하지 않고 와일드카드 또는 호스트 이름 URL 예약이 모두 없는 경우</span><span class="sxs-lookup"><span data-stu-id="de964-131">IPAddress specified does not match the IP address of a URL reservations AND neither a wildcard or host name URL reservation exist.</span></span>  
  
5.  <span data-ttu-id="de964-132">호스트 이름을 지정하는 URL 예약이 있으나 해당 호스트 이름이 인증서의 호스트 이름과 일치하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="de964-132">A URL reservation that specifies a host name exists, but the host name does not match the certificate host name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de964-133">요구 사항</span><span class="sxs-lookup"><span data-stu-id="de964-133">Requirements</span></span>  
 <span data-ttu-id="de964-134">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de964-134">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de964-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de964-135">See Also</span></span>  
 [<span data-ttu-id="de964-136">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="de964-136">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
