---
title: SetEmailConfiguration 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19068d7d7fff8c31c455ef76e8d2c2caa26b743f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737731"
---
# <a name="setemailconfiguration-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="1bed2-102">SetEmailConfiguration 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="1bed2-102">SetEmailConfiguration Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="1bed2-103">보고서 서버가 전자 메일을 보낼 때 사용할 전자 메일 배달 확장 프로그램을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-103">Configures the e-mail delivery extension used by the report server to send e-mail.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bed2-104">구문</span><span class="sxs-lookup"><span data-stu-id="1bed2-104">Syntax</span></span>  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bed2-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1bed2-105">Parameters</span></span>  
 <span data-ttu-id="1bed2-106">*SendUsingSMTPServer*</span><span class="sxs-lookup"><span data-stu-id="1bed2-106">*SendUsingSMTPServer*</span></span>  
 <span data-ttu-id="1bed2-107">전자 메일을 보내는 데 SMTP 서버를 사용하는지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-107">A Boolean value indicating whether the server is to use the SMTP server to send email.</span></span> <span data-ttu-id="1bed2-108">이 값은 true로만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-108">This value can only be set to true.</span></span> <span data-ttu-id="1bed2-109">기본값은 False입니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-109">Default value is false.</span></span>  
  
 <span data-ttu-id="1bed2-110">*SMTPServer*</span><span class="sxs-lookup"><span data-stu-id="1bed2-110">*SMTPServer*</span></span>  
 <span data-ttu-id="1bed2-111">SMTP 서버의 이름이나 IP 주소가 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-111">A string containing the name or IP address of an SMTP server.</span></span>  
  
 <span data-ttu-id="1bed2-112">*SenderEmailAddress*</span><span class="sxs-lookup"><span data-stu-id="1bed2-112">*SenderEmailAddress*</span></span>  
 <span data-ttu-id="1bed2-113">보고서 서버에서 보낸 전자 메일의 '받는 사람:' 필드에 사용된 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-113">The e-mail address used in the 'From:' field for e-mails sent from the report server.</span></span>  
  
 <span data-ttu-id="1bed2-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="1bed2-114">*HRESULT*</span></span>  
 <span data-ttu-id="1bed2-115">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bed2-116">Return Value</span><span class="sxs-lookup"><span data-stu-id="1bed2-116">Return Value</span></span>  
 <span data-ttu-id="1bed2-117">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="1bed2-118">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="1bed2-119">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bed2-120">설명</span><span class="sxs-lookup"><span data-stu-id="1bed2-120">Remarks</span></span>  
 <span data-ttu-id="1bed2-121">*SendUsingSMTPServer* 매개 변수를로 설정 하면 `true` 보고서 서버 구성 파일의 **sendusing** 항목이 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-121">When the *SendUsingSMTPServer* parameter is set to `true`, the **SendUsing** entry in the report server configuration file is set to 1.</span></span> <span data-ttu-id="1bed2-122">*SendUsingSMTPServer* 가로 설정 되 면 `false` **sendusing** 항목이 구성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-122">When *SendUsingSMTPServer* is set to `false`, the **SendUsing** entry is not configured.</span></span>  
  
 <span data-ttu-id="1bed2-123">이 메서드를 사용하면 보고서 서버 구성 파일의 **SendUsing** 항목을 1이 아닌 다른 값으로 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-123">This method does not provide a way for users to set the **SendUsing** entry in the report server configuration file to a value other than 1.</span></span> <span data-ttu-id="1bed2-124">SMTP 메일 외의 다른 항목에 대해 보고서 서버를 구성하려면 구성 파일을 수동으로 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bed2-124">To configure the report server for anything other than SMTP mail, you must edit the configuration file manually.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bed2-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1bed2-125">Requirements</span></span>  
 <span data-ttu-id="1bed2-126">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bed2-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bed2-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bed2-127">See Also</span></span>  
 [<span data-ttu-id="1bed2-128">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="1bed2-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
