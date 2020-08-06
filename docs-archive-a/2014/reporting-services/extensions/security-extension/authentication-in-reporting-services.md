---
title: Reporting Services의 인증 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], authentication
- forms-based authentication [Reporting Services]
- authentication [Reporting Services]
- custom authentication [Reporting Services]
ms.assetid: 103ce1f9-31d8-44bb-b540-2752e4dcf60b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59e97ba6ef849d8b4bfddfd6953c85826e351d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651522"
---
# <a name="authentication-in-reporting-services"></a><span data-ttu-id="c8f8d-102">Reporting Services의 인증</span><span class="sxs-lookup"><span data-stu-id="c8f8d-102">Authentication in Reporting Services</span></span>
  <span data-ttu-id="c8f8d-103">인증은 사용자의 권한을 ID에 설정하는 과정입니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-103">Authentication is the process of establishing a user's right to an identity.</span></span> <span data-ttu-id="c8f8d-104">사용자를 인증하는 데 사용할 수 있는 많은 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-104">There are many techniques that you can use to authenticate a user.</span></span> <span data-ttu-id="c8f8d-105">가장 일반적인 방법은 암호를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-105">The most common way is to use passwords.</span></span> <span data-ttu-id="c8f8d-106">예를 들어 폼 인증을 구현하는 경우 사용자에게 자격 증명을 요구(대개 로그인 이름과 암호를 요구하는 인터페이스를 통해 이루어짐)한 다음 데이터베이스 테이블이나 구성 파일과 같은 데이터 저장소와 대조하여 사용자를 검사하도록 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-106">When you implement Forms Authentication, for example, you want an implementation that queries users for credentials (usually by some interface that requests a login name and password) and then validates users against a data store, such as a database table or configuration file.</span></span> <span data-ttu-id="c8f8d-107">자격 증명을 확인할 수 없는 경우 인증 프로세스가 실패하고 사용자는 익명 ID를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-107">If the credentials can't be validated, the authentication process fails and the user will assume an anonymous identity.</span></span>  
  
## <a name="custom-authentication-in-reporting-services"></a><span data-ttu-id="c8f8d-108">Reporting Services의 사용자 지정 인증</span><span class="sxs-lookup"><span data-stu-id="c8f8d-108">Custom Authentication in Reporting Services</span></span>  
 <span data-ttu-id="c8f8d-109">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 Windows 운영 체제는 통합 보안을 통해 또는 사용자 자격 증명의 명시적인 수신과 검사를 통해 사용자 인증을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-109">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Windows operating system handles the authentication of users either through integrated security or through the explicit reception and validation of user credentials.</span></span> <span data-ttu-id="c8f8d-110">사용자 지정 인증은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 개발하여 추가 인증 체계를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-110">Custom authentication can be developed in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to support additional authentication schemes.</span></span> <span data-ttu-id="c8f8d-111">보안 확장 프로그램 인터페이스 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>을 통해 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-111">This is made possible through the security extension interface <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>.</span></span> <span data-ttu-id="c8f8d-112">모든 확장 프로그램은 보고서 서버에서 배포되고 사용되는 모든 확장 프로그램에 대한 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 기본 인터페이스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-112">All extensions inherit from the <xref:Microsoft.ReportingServices.Interfaces.IExtension> base interface for any extension deployed and used by the report server.</span></span> <span data-ttu-id="c8f8d-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension> 및 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>은 <xref:Microsoft.ReportingServices.Interfaces> 네임스페이스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension>, as well as <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>, are members of the <xref:Microsoft.ReportingServices.Interfaces> namespace.</span></span>  
  
 <span data-ttu-id="c8f8d-114">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 보고서 서버와 대조하여 인증하는 기본적인 방법은 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-114">The primary way to authenticate against a report server in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span> <span data-ttu-id="c8f8d-115">Reporting Services 웹 서비스의 이 멤버는 확인을 위해 사용자 자격 증명을 보고서 서버에 전달하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-115">This member of the Reporting Services Web service can be used to pass user credentials to a report server for validation.</span></span> <span data-ttu-id="c8f8d-116">기본 보안 확장 프로그램은 사용자 지정 인증 코드를 포함 하는 **Iauthenticationextension** 을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-116">Your underlying security extension implements **IAuthenticationExtension.LogonUser** which contains your custom authentication code.</span></span> <span data-ttu-id="c8f8d-117">폼 인증 예제에서는 제공된 자격 증명 및 데이터베이스의 사용자 지정 사용자 저장소와 대조하여 인증 검사를 수행하는 **LogonUser**가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-117">In the Forms Authentication sample, **LogonUser**, which performs an authentication check against the supplied credentials and a custom user store in a database.</span></span> <span data-ttu-id="c8f8d-118">**LogonUser**의 구현 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-118">An example of an implementation of **LogonUser** looks like this:</span></span>  
  
```  
public bool LogonUser(string userName, string password, string authority)  
{  
   return AuthenticationUtilities.VerifyPassword(userName, password);  
}  
  
```  
  
 <span data-ttu-id="c8f8d-119">다음 예제 함수는 제공된 자격 증명을 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-119">The following sample function is used to verify the supplied credentials:</span></span>  
  
```  
  
internal static bool VerifyPassword(string suppliedUserName,  
   string suppliedPassword)  
{   
   bool passwordMatch = false;  
   // Get the salt and pwd from the database based on the user name.  
   // See "How To: Use DPAPI (Machine Store) from ASP.NET," "How To:  
   // Use DPAPI (User Store) from Enterprise Services," and "How To:  
   // Create a DPAPI Library" for more information about how to use  
   // DPAPI to securely store connection strings.  
   SqlConnection conn = new SqlConnection(  
      "Server=localhost;" +   
      "Integrated Security=SSPI;" +  
      "database=UserAccounts");  
   SqlCommand cmd = new SqlCommand("LookupUser", conn);  
   cmd.CommandType = CommandType.StoredProcedure;  
  
   SqlParameter sqlParam = cmd.Parameters.Add("@userName",  
       SqlDbType.VarChar,  
       255);  
   sqlParam.Value = suppliedUserName;  
   try  
   {  
      conn.Open();  
      SqlDataReader reader = cmd.ExecuteReader();  
      reader.Read(); // Advance to the one and only row  
      // Return output parameters from returned data stream  
      string dbPasswordHash = reader.GetString(0);  
      string salt = reader.GetString(1);  
      reader.Close();  
      // Now take the salt and the password entered by the user  
      // and concatenate them together.  
      string passwordAndSalt = String.Concat(suppliedPassword, salt);  
      // Now hash them  
      string hashedPasswordAndSalt =  
         FormsAuthentication.HashPasswordForStoringInConfigFile(  
         passwordAndSalt,  
         "SHA1");  
      // Now verify them. Returns true if they are equal.  
      passwordMatch = hashedPasswordAndSalt.Equals(dbPasswordHash);  
   }  
   catch (Exception ex)  
   {  
       throw new Exception("Exception verifying password. " +  
          ex.Message);  
   }  
   finally  
   {  
       conn.Close();  
   }  
   return passwordMatch;  
}  
```  
  
## <a name="authentication-flow"></a><span data-ttu-id="c8f8d-120">인증 흐름</span><span class="sxs-lookup"><span data-stu-id="c8f8d-120">Authentication Flow</span></span>  
 <span data-ttu-id="c8f8d-121">Reporting Services 웹 서비스는 보고서 관리자 및 보고서 서버에 의한 폼 인증을 사용할 수 있도록 사용자 지정 인증 확장 프로그램을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-121">The Reporting Services Web service provides custom authentication extensions to enable Forms Authentication by Report Manager and the report server.</span></span>  
  
 <span data-ttu-id="c8f8d-122">Reporting Services 웹 서비스의 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 메서드는 인증을 위해 자격 증명을 보고서 서버에 제출하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-122">The <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of the Reporting Services Web service is used to submit credentials to the report server for authentication.</span></span> <span data-ttu-id="c8f8d-123">웹 서비스에서는 검사된 로그온 요청에 대해 HTTP 헤더를 사용하여 서버에서 클라이언트로 인증 티켓("쿠키"라고 함)을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-123">The Web service uses HTTP headers to pass an authentication ticket (known as a "cookie") from the server to the client for validated logon requests.</span></span>  
  
 <span data-ttu-id="c8f8d-124">다음 그림은 사용자 지정 인증 확장 프로그램을 사용하도록 구성된 보고서 서버와 함께 배포된 애플리케이션의 경우 웹 서비스에 사용자를 인증하는 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-124">The following illustration depicts the method of authenticating users to the Web service when your application is deployed with a report server configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="c8f8d-125">![Reporting Services 보안 인증 흐름](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services 보안 인증 흐름")</span><span class="sxs-lookup"><span data-stu-id="c8f8d-125">![Reporting Services security authentication flow](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services security authentication flow")</span></span>  
  
 <span data-ttu-id="c8f8d-126">그림 2에 나온 대로 인증 프로세스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-126">As shown in Figure 2, the authentication process is as follows:</span></span>  
  
1.  <span data-ttu-id="c8f8d-127">클라이언트 애플리케이션에서 사용자를 인증하도록 웹 서비스 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-127">A client application calls the Web service <xref:ReportService2010.ReportingService2010.LogonUser%2A> method to authenticate a user.</span></span>  
  
2.  <span data-ttu-id="c8f8d-128">웹 서비스는 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 보안 확장 프로그램의 메서드를 호출 합니다. 특히 **iauthenticationextension**을 구현 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-128">The Web service makes a call to the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of your security extension, specifically, the class that implements **IAuthenticationExtension**.</span></span>  
  
3.  <span data-ttu-id="c8f8d-129"><xref:ReportService2010.ReportingService2010.LogonUser%2A> 구현에서 사용자 저장소 또는 보안 기관에 있는 사용자 이름과 암호를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-129">Your implementation of <xref:ReportService2010.ReportingService2010.LogonUser%2A> validates the user name and password in the user store or security authority.</span></span>  
  
4.  <span data-ttu-id="c8f8d-130">인증이 성공하면 웹 서비스에서 쿠키를 만들고 세션을 위해 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-130">Upon successful authentication, the Web service creates a cookie and manages it for the session.</span></span>  
  
5.  <span data-ttu-id="c8f8d-131">웹 서비스는 HTTP 헤더에서 인증 티켓을 호출 애플리케이션에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-131">The Web service returns the authentication ticket to the calling application on the HTTP header.</span></span>  
  
 <span data-ttu-id="c8f8d-132">웹 서비스에서 보안 확장 프로그램을 통해 사용자를 성공적으로 인증하면 이후 요청에 사용되는 쿠키를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-132">When the Web service successfully authenticates a user through the security extension, it generates a cookie that is used for subsequent requests.</span></span> <span data-ttu-id="c8f8d-133">보고서 서버에 보안 기관이 포함되어 있지 않으므로 쿠키는 사용자 지정 보안 기관 내에 계속 유지되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-133">The cookie may not persist within the custom security authority because the report server does not own the security authority.</span></span> <span data-ttu-id="c8f8d-134">쿠키는 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 웹 서비스 메서드에서 반환되고 이후 웹 서비스 메서드 호출 및 URL 액세스에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-134">The cookie is returned from the <xref:ReportService2010.ReportingService2010.LogonUser%2A> Web service method and is used in subsequent Web service method calls and in URL access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8f8d-135">전송 중 쿠키의 노출을 피하려면 <xref:ReportService2010.ReportingService2010.LogonUser%2A>에서 반환된 인증 쿠키를 SSL(Secure Sockets Layer) 암호화를 사용하여 안전하게 전송해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-135">In order to avoid compromising the cookie during transmission, authentication cookies returned from <xref:ReportService2010.ReportingService2010.LogonUser%2A> should be transmitted securely using Secure Sockets Layer (SSL) encryption.</span></span>  
  
 <span data-ttu-id="c8f8d-136">사용자 지정 보안 확장 프로그램이 설치되어 있는 경우 URL 액세스를 통해 보고서 서버에 액세스하면 IIS(인터넷 정보 서비스) 및 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]에서 인증 티켓 전송을 자동으로 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-136">If you access the report server through URL access when a custom security extension is installed, Internet Information Services (IIS) and [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] automatically manage the transmission of the authentication ticket.</span></span> <span data-ttu-id="c8f8d-137">SOAP API를 통해 보고서 서버에 액세스하려는 경우에는 프록시 클래스 구현에서 인증 티켓 관리를 추가로 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-137">If you are accessing the report server through the SOAP API, your implementation of the proxy class must include additional support for managing the authentication ticket.</span></span> <span data-ttu-id="c8f8d-138">SOAP API를 사용하고 인증 티켓을 관리하는 방법은 "웹 서비스에서 사용자 지정 보안 사용"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-138">For more information about using the SOAP API and managing the authentication ticket, see "Using the Web Service with Custom Security."</span></span>  
  
## <a name="forms-authentication"></a><span data-ttu-id="c8f8d-139">폼 인증</span><span class="sxs-lookup"><span data-stu-id="c8f8d-139">Forms Authentication</span></span>  
 <span data-ttu-id="c8f8d-140">폼 인증은 인증되지 않은 사용자를 HTML 양식으로 지정하는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 인증 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-140">Forms Authentication is a type of [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in which an unauthenticated user is directed to an HTML form.</span></span> <span data-ttu-id="c8f8d-141">사용자가 자격 증명을 제공하면 인증 티켓이 포함된 쿠키가 발행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-141">Once the user provides credentials, the system issues a cookie containing an authentication ticket.</span></span> <span data-ttu-id="c8f8d-142">이후에 요청이 있으면 먼저 쿠키 검사를 통해 사용자가 보고서 서버에서 이미 인증되었는지 여부에 대한 확인이 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-142">On later requests, the system first checks the cookie to see if the user was already authenticated by the report server.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="c8f8d-143">는 Reporting Services API를 통해 사용 가능한 보안 확장성 인터페이스를 사용하여 폼 인증을 지원하도록 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-143">can be extended to support Forms Authentication using the security extensibility interfaces available through the Reporting Services API.</span></span> <span data-ttu-id="c8f8d-144">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]를 확장하여 폼 인증을 사용할 경우 보고서 서버와의 모든 통신에 대해 SSL(Secure Sockets Layer)을 사용하여 악의적인 사용자가 다른 사용자의 쿠키에 액세스하지 못하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-144">If you extend [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to use Forms Authentication, use Secure Sockets Layer (SSL) for all communications with the report server to prevent malicious users from gaining access to another user's cookie.</span></span> <span data-ttu-id="c8f8d-145">SSL을 사용하면 클라이언트와 보고서 서버 간의 상호 인증이 가능하며 이 두 컴퓨터 간의 통신 내용을 다른 컴퓨터에서 읽지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-145">SSL enables clients and a report server to authenticate each other and to ensure that no other computers can read the contents of communications between the two computers.</span></span> <span data-ttu-id="c8f8d-146">SSL 연결을 통해 클라이언트에서 전송되는 모든 데이터는 암호화되므로 악의적인 사용자가 보고서 서버로 전송된 암호나 데이터를 가로챌 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-146">All data sent from a client through an SSL connection is encrypted so that malicious users cannot intercept passwords or data sent to a report server.</span></span>  
  
 <span data-ttu-id="c8f8d-147">폼 인증은 일반적으로 Windows 이외의 플랫폼에 대한 계정 및 인증을 지원하기 위해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-147">Forms Authentication is generally implemented to support accounts and authentication for platforms other than Windows.</span></span> <span data-ttu-id="c8f8d-148">보고서 서버 액세스를 요청하는 사용자는 그래픽 인터페이스를 볼 수 있으며, 제공된 자격 증명은 인증을 위해 보안 기관에 제출됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-148">A graphical interface is presented to a user who requests access to a report server, and the supplied credentials are submitted to a security authority for authentication.</span></span>  
  
 <span data-ttu-id="c8f8d-149">폼 인증에서는 사람이 직접 자격 증명을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-149">Forms Authentication requires that a person is present to enter credentials.</span></span> <span data-ttu-id="c8f8d-150">Reporting Services 웹 서비스와 직접 통신하는 무인 애플리케이션의 경우 폼 인증에 사용자 지정 인증 체계를 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-150">For unattended applications that communicate directly with the Reporting Services Web service, Forms Authentication must be combined with a custom authentication scheme.</span></span>  
  
 <span data-ttu-id="c8f8d-151">폼 인증은 다음의 경우 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-151">Forms Authentication is appropriate for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] when:</span></span>  
  
-   <span data-ttu-id="c8f8d-152">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 계정이 없는 사용자를 저장하고 인증해야 하는 경우 및</span><span class="sxs-lookup"><span data-stu-id="c8f8d-152">You need to store and authenticate users that do not have [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows accounts, and</span></span>  
  
-   <span data-ttu-id="c8f8d-153">웹 사이트의 다양한 페이지 사이에서 고유의 사용자 인터페이스 양식을 로그온 페이지로 제공해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="c8f8d-153">You need to provide your own user interface form as a logon page between different pages on a Web site.</span></span>  
  
 <span data-ttu-id="c8f8d-154">폼 인증을 지원하는 사용자 지정 보안 확장 프로그램을 작성할 때 다음을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-154">Consider the following when writing a custom security extension that supports Forms Authentication:</span></span>  
  
-   <span data-ttu-id="c8f8d-155">폼 인증을 사용하는 경우 IIS(인터넷 정보 서비스)에서 보고서 서버 가상 디렉터리에 대해 익명 액세스를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-155">If you use Forms Authentication, anonymous access must be enabled on the report server virtual directory in Internet Information Services (IIS).</span></span>  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] <span data-ttu-id="c8f8d-156">인증은 폼 인증으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-156">authentication must be set to Forms.</span></span> <span data-ttu-id="c8f8d-157">보고서 서버의 경우 Web.config 파일에서 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 인증을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-157">You configure [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in the Web.config file for the report server.</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="c8f8d-158">는 Windows 인증 또는 사용자 지정 인증으로 사용자를 인증하고 권한을 부여할 수 있으며, 두 가지 인증을 모두 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-158">can authenticate and authorize users with either Windows Authentication or custom authentication, but not both.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="c8f8d-159">에서는 여러 보안 확장 프로그램을 동시에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8f8d-159">does not support simultaneous use of multiple security extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f8d-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8f8d-160">See Also</span></span>  
 [<span data-ttu-id="c8f8d-161">보안 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="c8f8d-161">Implementing a Security Extension</span></span>](../security-extension/implementing-a-security-extension.md)  
  
  
