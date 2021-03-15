========
Servlets
========

Code below shows using the DynamicReports within a servlet. The servlet will display a pdf document on the web browser.

.. code-block:: java
   :linenos:

    import static net.sf.dynamicreports.report.builder.DynamicReports.*;
    import java.io.IOException;
    import java.io.OutputStream;
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import net.sf.dynamicreports.report.exception.DRException;

    public class PdfReportServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;
    @Override
        protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            resp.setContentType("application/pdf");
            OutputStream out = resp.getOutputStream();
            try {
            report()
                ...
                .toPdf(out);
            } catch (DRException e) {
            throw new ServletException(e);
            }
            out.close();
        }
    }
